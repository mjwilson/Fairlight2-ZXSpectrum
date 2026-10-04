# Memory map (48K version)

The two parts share most of their layout. The font, the fill textures, the object-type table, the
 presets for the `C2` opcode, the player's frames and the saved fixed records are byte-for-byte the same.
 What differs is the template area (part 2 has more script
variables, so everything after them moves), the item list and the sprites.

## Overview

The Part column says whether a row applies to both parts or to one of them.

| Range | Size | Part | Contents |
|-------|------|------|----------|
| 6144-633F | 200 | both | Font: characters 20-5F, 8 bytes each |
| 6340-657F | 240 | both | Fill textures for the `DC` opcode: 18 patterns of 32 bytes |
| 6590-7767 | 11D8 | both | Code: graphics routines and the template interpreter, including the opcode table at 6C31-6CB0 |
| 7768-7A1C | 2B5 | both | Object-type table: 63 types (00-3E) of 11 bytes |
| 7A1D-7AE8 | CC | both | Room bounding-box presets for the `C2` opcode: presets 01-22 of 6 bytes (part 1 uses 01-0F, part 2 uses 01, 0C and 10-22) |
| 7AE9-7B6F | 87 | both | Unused (all zero) |
| 7B70-7BF8 | 89 | both | Engine variables and workspace, including the inventory |
| 7BF9-8FBA | 13C2 | both | Code: the game engine (objects, movement, collision, inventory, creature behaviour) |
| 8FEC-906D | 82 | 1 | Item sprites of types 34 and 35 |
| 8FEC-906D | 82 | 2 | *Not identified* |
| 906E-923B | 1CE | both | Item sprites |
| 923C-925F | 24 | both | *Not identified* |
| 9260-96BB | 45C | both | Player sprite frames |
| 96BC-9C8B | 5D0 | both | *Not identified* |
| 9C8C-9D17 | 8C | both | Saved copy of the floor, ceiling, wall and player records |
| 9D18-A0FF | 3E8 | both | Object records: floor, ceiling and walls, the player, then the room's objects |
| A100-B8FF | 1800 | both | Off-screen bitmap (where rooms are drawn: windows 2 and 4) |
| B900-BBFF | 300 | both | Off-screen attributes |
| BC00-BCFF | 100 | 1 | Unused (all zero) |
| BC00-BCFF | 100 | 2 | *Not identified* (31 non-zero bytes at BC08-BC6C) |
| BD00-BFFF | 300 | both | Item list, restart copy: 107 entries ending at BF82 in part 1, 81 ending at BEE6 in part 2 |
| C000-C09F | A0 | both | Interpreter state and the system variable slots 00-1F |
| C0A0-C0C7 | 28 | 1 | Script variables 20-33 |
| C0C8-C1F7 | 130 | 1 | Template table: 151 templates plus an end entry |
| C1F8-E062 | 1E6B | 1 | Templates 00-96, including the live item list at D556-D7D8 (template 64) |
| E063-E23F | 1DD | 1 | *Not identified* |
| E240-E69B | 45C | 1 | Witch sprite frames (swapped with the player's frames) |
| E69C-FFFF | 1964 | 1 | Scenery and creature sprites |
| C0A0-C0DB | 3C | 2 | Script variables 20-3D |
| C0DC-C1FF | 124 | 2 | Template table: 145 templates plus an end entry |
| C200-DEA9 | 1CAA | 2 | Templates 00-90, including the live item list at D5ED-D7D3 (template 64) |
| DEAA-E4DF | 636 | 2 | Unused (all zero) |
| E4E0-FFFF | 1B20 | 2 | Scenery and creature sprites, and the carpet-riding frames |

## Screen and system area (4000-657F)

- **6144-633F** is the font. Only characters 20-5F (space, digits, punctuation and capitals) are
  stored, so the game has no lowercase text.
- **6340-657F** holds the fill textures used by the `DC` opcode (pointer at C01E). Each is a 16×16 tile of
  32 bytes. Part 1 uses textures up to 11, and part 2 up to 10.

## Code (6590-8FBA)

The code is in two blocks, with the main data tables between them:

- **6590-7767**: low-level graphics (pixel addressing, plotting, lines, flood fill, sprites,
  windows, text) and the template interpreter. The opcode jump table for C0-FF is at **6C31-6CB0**.
  See [room_format.md](room_format.md).
- **7BF9-8FBA**: the game engine: object placement and movement, collision (8B7E), the inventory,
  potion and carpet, fighting and creature behaviour. See [objects.md](objects.md) and
  [dynamic_objects.md](dynamic_objects.md).

## Engine tables and variables (7768-7BF8)

- **7768-7A1C, object-type table.** 11 bytes per type: screen position, sprite size and address,
  size in x, y and z, class and carry value. Type n is at 7768 + 11n. Types 36-3E are the
  doorways placed by `D5`. The table is the same in both parts, but a type's sprite only exists in
  the part that uses it. See [dynamic_objects.md](dynamic_objects.md).
- **7A1D-7AE8, `C2` presets.** Preset n (01-22) is the 6 bytes at 7A17 + 6n: the floor and ceiling
  heights and the positions of the four walls. There is no preset 00: its slot (7A17-7A1C) is the
  end of type 3E.
- **7B70-7BF8, engine variables.** The start-up template (part 1: 69, part 2: 75) clears
  7B70-7BD3. The ones identified so far:

| Address | Contents | Part 1 | Part 2 |
|---------|----------|--------|--------|
| 7B70 | Number of object records in use | | |
| 7B77 | Message status byte | | |
| 7B79 | Magic potion uses left | 10 | 0 (no magic potion) |
| 7B7A | Magic carpet uses left | 0 (no carpet) | 10 |
| 7B82 | Load being carried | | |
| 7B83 | Carry limit | 8 | 9 |
| 7B85 | Energy | | |
| 7B86 | Player's form (bit 0 transformed, bit 1 carpet) | | |
| 7B87 | Engine flags (bit 2: first tick in a new room) | | |
| 7B88-7B8D | Creature hit counters | | |
| 7B8E | Selected inventory slot (low byte of its address) | | |
| 7B8F-7B98 | Inventory: 5 slots, each a pointer to an object record | | |
| 7BA4 | Current room | starts at 02 | starts at 05 |

## Sprites

The object-type table points at the first frame of each sprite. Each sprite is stored as its
bitmap followed by a mask of the same size. Gaps between the listed sprites hold the further
animation frames of creatures.

- **8FEC-923B, items.** 906E-923B is the same in both parts, so the objects carried from part 1 to
  part 2 can be drawn in both: the magic wand (type 29, 91A4), the sword (08, 90F6) and the keys
  (0E, 91C0). Part 1's magic potion (2A, 90DA) and part 2's potion (2B, 908A) and bottle (09, 91D4)
  are here too. 8FEC-906D holds types 34 and 35 in part 1, and something else in part 2.
- **9260-96BB, the player**, the same in both parts.
- **Part 1, E240-E69B: the witch.** Using the magic potion swaps these 45C bytes with the player's
  frames at 9260 (8968).
- **Part 1, E69C-FFFF: scenery and creatures**, from the wolf (type 21, E69C) to the second
  door-frame graphic (type 39, FECE-FFFF), including the parts the trees are built from (types 00,
  03, 04, 06 and 07).
- **Part 2, E4E0-FFFF: scenery and creatures**, starting with the magic carpet (type 30, E4E0), the
  book (32), the disk (2F) and the ogre (12), and including the bat, spiky ball, monk, skeleton,
  table, stool, moving block, guard and the door frames.
- **Part 2, EB84 and EC92: carpet riding.** While the player is on the carpet, the animation takes
  40×27 frames from EB84 or EC92, depending on the direction faced (see
  [Magic potion and magic carpet](dynamic_objects.md#magic-potion-and-magic-carpet)).

So the potion only works in part 1 and the carpet only in part 2: each part has the graphics for
just one of them, although the code for both is in each part.

## Object records (9C8C-A0FF)

Every object in the current room has a 20-byte record. See
[Object record](dynamic_objects.md#object-record-20-bytes).

| Range | Contents |
|-------|----------|
| 9C8C-9D17 | Saved copy of the 7 fixed records below. The restart template (part 1: 6A, part 2: 83) copies it back. |
| 9D18-9D8F | The room's floor (9D18), ceiling (9D2C), x walls (9D40, 9D54) and z walls (9D68, 9D7C): invisible boxes sized by `C2` |
| 9D90-9DA3 | The player |
| 9DA4- | The room's objects, in the order they were placed. 7B70 counts the records in use. |

## Off-screen buffer (A100-BBFF)

A second screen with the Spectrum layout. Windows 2 (the whole buffer) and 4 (the play area) have
offset 61, so they draw here rather than on the display. **A100-B8FF** is the bitmap and
**B900-BBFF** the attributes. `F7` also uses B900 when it wraps a scroll round.

## Item list

Each entry is 6 bytes: location, type, flags, x, y, z. The list ends with location FF. See
[Item list entries](dynamic_objects.md#item-list-entries). There are two copies:

- **The live list**, pointed to by C05B: D556-D7D8 in part 1 and D5ED-D7D3 in part 2. In both parts
  it is kept in the template area as template 64, so it is saved with the rest of the game. It is
  data, not script.
- **BD00-BFFF, the restart copy.** The start-up template (part 1: 69, part 2: 75) copies the list
  here (300 bytes) once, and the restart template (part 1: 6A, part 2: 83) copies it back every time
  the game is started or restarted. Part 2's restart template also runs the part 1 handover the
  first time; see [Part 1 to part 2 handover](objects.md#part-1-to-part-2-handover).

## Interpreter state and templates (C000 up to the end of the templates)

| Range | Contents |
|-------|----------|
| C000-C05F | Interpreter state: the end-marker address (C000) and saved byte (C00D), the template-table pointer (C008), texture pointer (C01E), colour (C022), drawing flags (C023, C024), line pattern (C026), attribute mask (C027), text position (C028), character advance and font (C02C, C02D), the current window (C030-C036), the pen, line start and windows 1-5 (C037-C054), the `C3` position (C055-C057), the item-list pointer (C05B), the room (C05D) and the object counter (C05E) |
| C060-C09F | Variable slots 00-1F. These overlap interpreter workspace, such as the origin for absolute coordinates (C062, C063) and the flood fill's workspace (C074-C07F). |
| C0A0- | Script variables from 20: 20-33 in part 1 (C0A0-C0C7), 20-3D in part 2 (C0A0-C0DB) |
| C0C8 / C0DC | Template table (part 1 / part 2): the start address of each template, with a final entry marking the end of the last one |
| C1F8 / C200 | The templates (part 1 / part 2). See [part1/templates.md](part1/templates.md), [part2/templates.md](part2/templates.md) and [room_format.md](room_format.md). |

The script variables are named in template 00. Both parts have A, B, C, D, LIFE, X, Y, Z, N0-N5,
E, F, X1, Y1 and Z1. Part 1 then has ROOM (33). Part 2 has A1, ROOM, N15, N6, N7, N8, N9, N13, AA
and KEY (33-3C), and var3D has no name. The N variables are constants holding the number in their
name.

Within the templates:

- **Part 1** (00-96): template 00 holds the variable names, 02-49 are the rooms, 4A is the "falling
  off a cliff" effect, and the rest are building blocks, menus, the main loop (6A) and the end of
  part 1 (95, which loads part 2).
- **Part 2** (00-90): template 00 holds the variable names, 01 is the start-up script, the rooms run
  up to 52 (which ends part 2), and the rest are building blocks (including the pit templates 25
  and 45), menus, the main loop (83) and the end of part 2 (87).
