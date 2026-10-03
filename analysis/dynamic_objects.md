# Dynamic objects

By "dynamic objects" I mean both collectable objects and enemies. These are
held in the same data structure.

Each object has a 6-byte data structure. The first byte holds the room number
which the object is in. The second byte identifies the type of object.

There is a primary copy of the object data at BD00. At the start of the game,
this is copied to an in-game copy of the data (the address is held in C05B). The
copy is made again every time the game restarts (template 6A in part 1, 83 in
part 2), which is why objects return to their starting places after the player
dies.

When the player enters a room, the in-game table is scanned, and other data
structures are created to represent the live view of the objects. When the
player exits, then the table is updated with the latest information (such as
a new position).

 * [Details of objects in part 1](./part1/dynamic_objects.md).
 * [Details of objects in part 2](./part2/dynamic_objects.md).

The type table and the game code described below are the same in both parts. Only the
object lists differ.

## Item list entries

```
<location> <type> <flags> <x> <y> <z>     ; 6 bytes per entry, list ends with location FF
```

- **Location.** A room number. FE means the object is not in any room: it is being carried, or
  it has been killed.
- **Type.** An index into the object-type table (see below).
- **Flags.** Copied into byte 12 of the object's record. See
  [Kind and flags](#kind-and-flags-record-byte-12).
- **x, y, z.** The object's position in the room. World y increases upwards and is the top of the
  object; the floor is at y = 32.

When the player enters a room, opcode `CB` places every entry whose location equals the room. It
builds a 20-byte object record for each one, and stores the entry's 1-based position in the list
in the record's byte 19. That link is how the game writes changes back into the list:

- when an object is picked up or killed, its location is set to FE;
- when an item is dropped, its location is set to the current room (7BA4, at 8001);
- when the player leaves a room (8482), the current x, y and z of every object in the room are
  written back, so items and creatures stay where they were left.

Objects that start out overlapping are tidied up. The room-entry template sets bit 2 of 7B87
for the first tick in a new room. During that tick, if an object overlaps another movable object
(one whose byte 16 is not 0), the other object is flagged as taken and erased (84F2, 8574). The
flag is cleared afterwards. The removal is not written back to the list, so it happens again on
every visit.

`CB` also resets six hit counters (7B88-7B8D) to 4. The engine gives one to each creature in the
room, so a creature needs 4 counted hits to kill.

## Object-type table (7768, 11 bytes per entry)

The type byte selects an 11-byte entry at 7768 + 11 x type. When an object is placed, most of the
entry is copied into its record:

| Byte | Copied to record byte | Meaning |
|------|-----------------------|---------|
| 0 | 0 | Sprite screen x (pixels) at the reference position |
| 1 | 1 | Sprite screen y at the reference position |
| 2 | 2 | Sprite width in pixels (the blitter uses `(b & F8) >> 3` bytes) |
| 3 | 3 | Sprite height in lines |
| 4-5 | 4-5 | Sprite graphic address (0000 means invisible) |
| 6-8 | 9-11 | Bounding-box size in x, y and z |
| 9 | 13, 14 | Class: selects the object's behaviour (see below) |
| 10 | 16 | Carry value: weight for items, mass for anything that moves (see below) |

The reference position is where the sprite appears when the object is at world (32, 32 + ysize,
32), i.e. standing on the floor at the origin. The actual screen position is worked out from the
difference between the object's position and that point.

**Class** (byte 9). For a creature this selects its behaviour routine (7D6C-7EC7): for example
classes 4, 6, 7, 9, 0B and 0E chase the player, and class 0D moves in random directions. When the
object is placed, byte 13 of its record is set from the class's low nibble: class 1 gives 07,
class 2 gives 02, class 0C gives 82, and classes 04-0B and 0D-0F give 05 (which also set byte 17
to 10). Any other class gives 00.

## Object record (20 bytes)

The records of the objects in the current room start at 9DA4. The six records before that
(9D18-9D8F) are invisible slabs that form the room's walls, floor and ceiling, and 9D90 is the
player.

| Offset | Contents |
|--------|----------|
| 0-1 | Screen x, y (after projection) |
| 2-3 | Sprite width (pixels), height (lines) |
| 4-5 | Sprite address |
| 6-8 | World x, y, z |
| 9-11 | Size in x, y, z |
| 12 | Kind and flags: the `<flags>` byte from the item list |
| 13 | Derived from the class (see above) |
| 14 | Class (from the type table) |
| 15 | Set to 1 when placed. Used as a timer by the behaviour routines, and as the length of a push. |
| 16 | Carry value from the type table: bits 0-4 are the weight/mass value, and bit 5 is set once the object is taken |
| 17 | 10 for the item classes. Used as an animation-frame counter. |
| 18 | Direction of a push. For a doorway, its lock. |
| 19 | The object's 1-based position in the item list (00 for scenery placed by `C1`) |

## Kind and flags (record byte 12)

The `<flags>` byte holds two separate fields:

- **the high nibble** is a set of flag bits;
- **the low nibble** is the object's kind.

| Value | Where it is checked | Meaning |
|-------|---------------------|---------|
| bit 4 (10) | 852C, 84FF | When the player walks into the object, or the object moves into the player, the player loses 10 energy (7CDF) and the object is destroyed |
| bit 5 (20) | 805C | Can be picked up. The pick-up routine (8021-80C3) only considers objects with this bit set, so every portable item has it. |
| bit 6 (40) | 8566 | Can be killed. Each tick that the player touches the object while the sword is out, the object's hit counter goes down by 1. At 0 the object is removed: bit 5 of byte 16 is set, and its location in the item list is set to FE. |
| bit 7 (80) | 855D, 8846 | Hurts the player: 1 energy is lost on each tick of contact. While the player is fighting, this only happens when the sword is back. Every creature has this bit. |
| low nibble 1 | 831B | Exit or doorway (used by the doorway objects that the room templates place, not in the item lists) |
| low nibble 2 or 3 | 8697, 862B | A special collision response on one horizontal axis (used by invisible collision boxes) |
| low nibble 7 | 85D2 | Destroys whatever touches it (not used by the dynamic objects; it is used for deadly floors, see [objects.md](objects.md#deadly-floors)) |
| low nibble of a portable item | 8949 | What the item does when used. See [Using items](#using-items). |

The combinations used by the dynamic objects are:

| Byte | Meaning |
|------|---------|
| 00 | Fixed object: cannot be picked up, does not hurt |
| 20 | Portable item |
| 24, 26, 2A, 2C, 2D, 2F | Portable item with a use-key action (the kind is the low nibble) |
| 2E | Portable item of kind E |
| 80 | Creature that hurts but cannot be killed by fighting (a kind C weapon can still destroy it) |
| 90 | Hurts, and touching it costs 10 energy and destroys it |
| A0 | Hurts, and is flagged as portable (but may be too heavy to pick up) |
| C0 | Creature that hurts and can be killed |

## Weight, mass and the "taken" flag (record byte 16)

Byte 16 comes from byte 10 of the type table. Its low 5 bits are used in two ways.

- **Fixed objects.** If bits 0-4 are 0, the object is fixed, and the game skips it when moving
  objects.
- **Weight** (for items). When the player picks something up (8062), the weight is
  `(byte16 & 1F) - 10` (0 if that goes negative). The weight is added to the player's current
  load at 7B82. If the total would be equal to or more than the limit at 7B83 (8 in part 1, 9 in part
  2, set on every room entry), the pick-up fails, and the "TOO HEAVY" message is shown. The values used are 10, 13, 14, 16 and 18, which
  are weights 0, 3, 4, 6 and 8. In part 1 an object of weight 8 can never be picked up. In part 2 it can, but only when everything
  else being carried weighs 0.
- **Mass** (for anything that moves). When a moving object bumps into another (875E-877D), the
  target is shoved if **mover's mass + 5 >= target's mass**. The shove lasts
  **(mover's mass + 5 - target's mass) + 1** ticks, stored in the target's byte 15, and bit 7 of
  its byte 14 is set. While it is being shoved, the object moves in the pusher's direction (stored
  in its byte 18) instead of following its behaviour routine or the player's controls. The player
  has mass 12, so creatures of mass 14, 16 and 18 are progressively harder to shove, and shove
  the player further.
- **Taken flag.** Bit 5 is set when the object is picked up or killed. After that, the game
  ignores the object.

## Using items

The player has five inventory slots (7B8F-7B98), selected with keys 1-5. The use key (checked at
8930) acts on the item in the selected slot. What happens depends on the item's kind, which is the
low nibble of its flags byte:

| Kind | Effect |
|------|--------|
| 4 | Energy + 10, capped at 99. The item is used up. |
| 5 | Sets bit 7 of 7B87. The item is used up. |
| 6 | Energy set to 99. The item is used up. |
| A | If the player is in room 0E, moves them to room 64. In part 1 this ends the part. |
| C | Turns the item into a weapon: its class (byte 14) becomes 12. See [Weapons (kind C)](#weapons-kind-c). |
| D | Magic carpet: toggles carpet mode. The number of uses left is in 7B7A. |
| F | Magic potion: toggles witch mode. The number of uses left is in 7B79. |

Any other kind does nothing when used.

### Weapons (kind C)

Using a kind C item changes its class to 12 (89D0). The low nibble, 2, selects a behaviour
routine (7D7B) that makes the item move on its own once it has been dropped. Each tick it takes
its direction from the player's record (byte 14, at 9D9E), so it moves the way the player is
moving, and the player can steer it. It also alternates between two animation frames.

When a moving kind C object hits another object that has a class (8597-85CA), both are destroyed
(location FE, taken flag set). This does not depend on the target's "can be killed" flag or its
hit counter, so it kills creatures that the sword cannot, such as part 2's monks. Each weapon is
used up by its first kill. If the object it hits is the player (class 8), the player's energy is
set to 0.

Before it is used, the item's class is 0, so it does not move and harms nothing.

The kill needs the two bounding boxes to overlap, like any collision. A weapon moving above a low
creature passes over it without touching it. In part 2, for example, the spiky ball cannot hit
the disks.

### Magic potion and magic carpet

Each part sets its item's use count to 10. Each use toggles the form and uses up one charge. When
the count reaches 0, the item is removed from its slot (8A16).

The player's form is held in **7B86**. Bit 0 means "transformed" and is set by both items.
Bit 1 means "carpet".

**Potion: witch (8968).** The witch's frames replace the player's frames in place. 8968 swaps
45C bytes between the player's sprite area at 9260 and the witch graphics at E240, then flips
bit 0 of 7B86. Using the potion again swaps them back. The sprite size and address in the
player's record are unchanged, because the witch frames are the same shape. Bit 0 then changes
behaviour:

- the animation uses a different frame count (7C30);
- the carrying frames are not used (7F37, 7F4C);
- the pick-up key is ignored (7F6D);
- the fighting animation is skipped (8140);
- creatures of class 7 (the wolves) stop homing in on the player (87E1: the direction-finding
  routine returns early), and their movement is changed (7EAE).

This is the "repels wolves" effect.

**Magic carpet (89AA).** The carpet uses a separate set of frames, not a swap. 89AA flips bits 0
and 1 of 7B86 (XOR 3), and rewrites the player record's sprite width and height (bytes 2-3, at
9D92): 24x31 normally, or 40x27 on the carpet. While bit 1 is set:

- the animation routine takes its frames from EB84, with 4 frames (7C1C);
- the walking frames are EB84 or EC92, depending on the direction faced (7F1E);
- the player's controls are handled differently (7EDA, 810A), which probably allows flying.

The collision box (bytes 9-11) is **not** changed. The carpet also sets bit 0, so the
"transformed" restrictions (no pick-up, no fighting) apply on the carpet too.

**Undoing it.** Before the engine hands back to the script, for the quit menu (Space + Symbol
Shift) or because energy has reached 0, 8467 checks 7B86. If the carpet is on, it calls 89AA; if
the witch is on, it calls 8968. This puts the player back to normal. It matters for the potion in
particular, because its swap changes the sprite data itself. Without it, a saved game or a
restart would keep the witch graphics in the player's sprite area.
