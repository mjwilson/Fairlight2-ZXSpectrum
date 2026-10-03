# Dynamic objects

There is a primary copy of the object data at BD00. At the start of the game,
this is copied to D556, which is the in-game copy of the data.

```
bd00: 02 2a 2f 82 8c 78 ; magic potion
bd06: 35 0e 20 a8 48 38 ; key
bd0c: 49 0e 20 ce 4a 5e ; key
bd12: 38 0e 20 72 34 32 ; key
bd18: 46 0e 20 90 34 32 ; key
bd1e: 02 0e 20 76 34 a6 ; key
bd24: 2f 0e 20 32 34 6c ; key
bd2a: 04 21 c0 72 46 96 ; wolf
bd30: 04 09 24 72 3e 5c ; bottle
bd36: 05 0f 20 50 3a 7e ; rock
bd3c: 05 0f 20 50 3a 6c ; rock
bd42: 05 0b 20 74 3a 4e ; rock
bd48: 05 0b 20 68 3a 70 ; rock
bd4e: 05 0c 20 56 38 4a ; rock
bd54: 05 0c 20 46 38 5a ; rock
bd5a: 06 23 c0 94 4a 42 ; guard
bd60: 08 21 c0 76 46 5e ; wolf
bd66: 09 21 c0 92 46 98 ; wolf
bd6c: 0a 0b 20 52 3a 76 ; rock
bd72: 0b 0f 20 56 3a 64 ; rock
bd78: 0b 0c 20 44 38 94 ; rock
bd7e: 0b 0b 20 88 3a 66 ; rock
bd84: 0b 0b 20 5a 3a 80 ; rock
bd8a: 0e 23 c0 82 4a 9a ; guard
bd90: 0f 21 c0 7e 46 5e ; wolf
bd96: 12 09 24 36 3e 36 ; bottle
bd9c: 14 0c 20 88 38 a4 ; rock
bda2: 14 0f 20 44 3a 84 ; rock
bda8: 14 0f 20 80 3a a6 ; rock
bdae: 14 0c 20 7a 38 78 ; rock
bdb4: 14 0b 20 aa 3a 60 ; rock
bdba: 15 23 c0 78 4a a2 ; guard
bdc0: 16 21 c0 66 46 9c ; wolf
bdc6: 17 21 c0 62 46 8a ; wolf
bdcc: 18 0c 20 44 38 94 ; rock
bdd2: 18 0b 20 68 3a 60 ; rock
bdd8: 19 09 24 6e 3e 62 ; bottle
bdde: 1a 24 c0 4a 4a 3e ; guard
bde4: 1c 02 90 63 42 50 ; bubble
bdea: 1c 08 20 a6 48 84 ; barrel
bdf0: 1c 08 20 9a 48 84 ; barrel
bdf6: 1d 23 c0 88 4a 82 ; guard
bdfc: 1e 25 c0 76 4a 8a ; guard 
be02: 1e 21 c0 9c 46 5e ; wolf
be08: 1f 08 20 44 48 3a ; barrel
be0e: 20 02 90 3e 42 87 ; bubble
be14: 23 21 c0 7e 46 5e ; wolf
be1a: 23 25 c0 9c 4a 94 ; guard
be20: 24 2b 26 68 6a 36 ; potion
be26: 24 33 00 94 3c 32 ; moving block
be2c: 24 33 00 94 46 32 ; moving block
be32: 24 33 00 94 50 32 ; moving block
be38: 26 23 c0 94 4a 7e ; guard
be3e: 27 23 c0 8c 4a 74 ; guard
be44: 28 2b 26 68 6a 4a ; potion
be4a: 28 33 00 94 3e 32 ; moving block
be50: 28 33 00 94 4a 32 ; moving block
be56: 28 33 00 94 56 32 ; moving block
be5c: 2a 23 c0 5a 4a 94 ; guard
be62: 2d 23 c0 60 4a 8e ; guard
be68: 2e 23 c0 62 4a 66 ; guard
be6e: 2f 08 20 8e 48 68 ; barrel
be74: 2f 08 20 8a 48 82 ; barrel
be7a: 2f 08 20 80 48 56 ; barrel
be80: 2f 08 20 9e 48 56 ; barrel
be86: 2f 0c 20 3c 38 7a ; rock
be8c: 2f 0f 20 32 3c 6e ; rock
be92: 2f 0f 20 34 42 74 ; rock
be98: 2f 0c 20 32 38 7a ; rock
be9e: 2f 0b 20 32 3a 74 ; rock
bea4: 30 23 c0 76 4a 86 ; guard
beaa: 31 31 2a 8a 36 64 ; sword
beb0: 32 29 2e 82 3c 6e ; magic wand
beb6: 32 08 20 72 48 a4 ; barrel
bebc: 32 1f 24 72 4e aa ; chicken
bec2: 33 23 c0 8e 4a 52 ; guard
bec8: 35 1f 24 aa 4c 4e ; chicken
bece: 35 1f 24 ac 4c 38 ; chicken
bed4: 36 02 90 61 42 60 ; bubble
beda: 37 33 00 6e 5a 60 ; moving block
bee0: 37 09 24 78 66 68 ; bottle
bee6: 38 08 20 72 4a 32 ; barrel
beec: 3a 23 c0 5a 4a 60 ; guard
bef2: 3b 21 c0 3e 46 64 ; wolf
bef8: 3b 23 c0 6a 4a 46 ; guard
befe: 3c 02 90 73 42 78 ; bubble
bf04: 3c 02 90 7f 42 68 ; bubble
bf0a: 3d 23 c0 98 4a 70 ; guard
bf10: 3e 23 c0 72 4a b8 ; guard
bf16: 41 23 c0 78 4a 8e ; guard
bf1c: 42 08 20 a6 48 84 ; barrel
bf22: 42 08 20 9a 48 84 ; barrel
bf28: 45 02 90 64 42 81 ; bubble
bf2e: 46 0c 20 80 38 74 ; rock
bf34: 46 0f 20 3a 3a 66 ; rock
bf3a: 46 0c 20 3a 38 6c ; rock
bf40: 46 1f 24 8e 38 3a ; chicken
bf46: 46 23 c0 4e 4a 82 ; guard
bf4c: 46 25 c0 4e 4a 82 ; guard 
bf52: 47 1f 24 9c 38 98 ; chicken
bf58: 47 1f 24 9c 38 90 ; chicken
bf5e: 47 09 24 9c 3e a2 ; bottle
bf64: 48 0c 20 98 38 74 ; rock
bf6a: 48 0f 20 50 3a 78 ; rock
bf70: 48 08 20 94 48 66 ; barrel
bf76: 49 08 20 c6 48 5e ; barrel
bf7c: 49 23 c0 96 4a 6c ; guard
bf82: ff
```

Each entry is `<room> <type> <flags> <x> <y> <z>`. See [the general description](../dynamic_objects.md)
for what the fields mean.

## Object types in part 1

The attributes come from the object-type table at 7768 (see
[Object-type table](../dynamic_objects.md#object-type-table-7768-11-bytes-per-entry)).

| Type | Name | Image | Flags | Meaning of the flags | Sprite | Size (x, y, z) | Class | Byte 16 |
|------|------|-------|-------|----------------------|--------|----------------|-------|---------|
| 02 | bubble | [![02](sprites/type_02_bubble.png)](sprites/type_02_bubble.png) | 90 | Touching it costs the player 10 energy and pops it (bit 4); it also hurts on contact (bit 7) | 24x21 | 0A 10 0A | 03 | 10 |
| 08 | barrel | [![08](sprites/type_08_barrel.png)](sprites/type_08_barrel.png) | 20 | Portable | 24x29 | 0C 16 0E | 00 | 16 (weight 6) |
| 09 | bottle | [![09](sprites/type_09_bottle.png)](sprites/type_09_bottle.png) | 24 | Portable; energy + 10 when used | 16x16 | 06 0C 06 | 00 | 10 (weight 0) |
| 0B, 0C, 0F | rock | [![0B](sprites/type_0B_rock.png)](sprites/type_0B_rock.png) [![0C](sprites/type_0C_rock.png)](sprites/type_0C_rock.png) [![0F](sprites/type_0F_rock.png)](sprites/type_0F_rock.png) | 20 | Portable | 16x12 to 16x14 | 06 06-08 06 | 00 | 0B, 0C: 16 (weight 6); 0F: 10 (weight 0) |
| 0E | key | [![0E](sprites/type_0E_key.png)](sprites/type_0E_key.png) | 20 | Portable (opens doors) | 16x5 | 04 02 08 | 00 | 10 (weight 0) |
| 1F | chicken | [![1F](sprites/type_1F_chicken.png)](sprites/type_1F_chicken.png) | 24 | Portable; energy + 10 when used | 16x10 | 06 06 08 | 00 | 10 (weight 0) |
| 21 | wolf | [![21](sprites/type_21_wolf.png)](sprites/type_21_wolf.png) | C0 | Creature: hurts, can be killed | 40x30 | 10 14 10 | 07 | 16 (mass) |
| 23 | guard | [![23](sprites/type_23_guard.png)](sprites/type_23_guard.png) | C0 | Creature: hurts, can be killed | 24x26 | 0A 18 0A | 06 | 14 (mass) |
| 24, 25 | guard | [![24](sprites/type_24_guard.png)](sprites/type_24_guard.png) [![25](sprites/type_25_guard.png)](sprites/type_25_guard.png) | C0 | Creature: hurts, can be killed | 24x26 | 0A 18 0A | 09 | 14 (mass) |
| 29 | magic wand | [![29](sprites/type_29_magic_wand.png)](sprites/type_29_magic_wand.png) | 2E | Portable, kind E | 16x7 | 0C 04 06 | 00 | 10 (weight 0) |
| 2A | magic potion | [![2A](sprites/type_2A_magic_potion.png)](sprites/type_2A_magic_potion.png) | 2F | Portable; turns the player into a witch when used | 16x7 | 06 06 06 | 00 | 10 (weight 0) |
| 2B | potion | [![2B](sprites/type_2B_potion.png)](sprites/type_2B_potion.png) | 26 | Portable; energy set to 99 when used | 16x10 | 06 08 06 | 00 | 10 (weight 0) |
| 31 | sword | [![31](sprites/type_31_sword.png)](sprites/type_31_sword.png) | 2A | Portable; used in room 0E, it ends part 1 | 16x7 | 0C 04 06 | 00 | 10 (weight 0) |
| 33 | moving block | [![33](sprites/type_33_moving_block.png)](sprites/type_33_moving_block.png) | 00 | Fixed (cannot be picked up) | 40x23 | 10 06 10 | 01 | 18 |

## Notes

- **Item ids.** An object's id is its 1-based position in this list: the magic potion (BD00) is
  item 1, and the magic wand (BEB0) is item 49 (hex; the 73rd entry). A door's lock stores the id of its key minus 1,
  so the keys (items 2-7) open locks 1-6.
- **Guards (types 23, 24 and 25).** All three use the same sprite, size and mass. They differ in
  class, which selects the behaviour routine: type 23 is class 6, which only chases the player
  when it is near and otherwise keeps walking in its current direction; types 24 and 25 are
  class 9, which always chases. In room 46 the list has a type 23 and a type 25 guard at exactly
  the same position (4E, 4A, 82), but only one guard ever appears. On the first tick after the
  player enters a room, bit 2 of 7B87 is set (by the room-entry template). If an object then
  overlaps another movable object, the other one is flagged as taken and erased (84F2, 8574).
  The flag is cleared after that tick. So one of the two guards is removed as soon as the room is
  set up, probably the type 25 one, since the type 23 guard comes first and is processed first.
  This is not written back to the list as location FE, so it happens again on every visit.
- **Wolves (type 21)** are class 7. While the player is a witch, class 7 creatures stop homing in
  on the player, which is how the magic potion repels wolves. They are heavier than the guards
  (mass 16 against 14), so they are harder to shove.
- **The magic potion** has 10 uses (7B79 is set to 10 by template 6A). See
  [Magic potion and magic carpet](../dynamic_objects.md#magic-potion-and-magic-carpet).
- **The sword (type 31, kind A)** moves the player to room 64 when used in room 0E. Room 64 ends
  part 1 and loads part 2.
- **The magic wand (type 29)** does nothing when used in part 1. Nothing in part 1's code checks for it (for example, it gives no protection from bubbles). Carried into part 2, it becomes
  the key to the door from room 50 to room 51 (see
  [part 2](../part2/dynamic_objects.md#notes)).
- **Barrels and the heavier rocks** (types 0B and 0C) weigh 6, so with the carry limit of 8 the
  player can carry only one of them at a time.