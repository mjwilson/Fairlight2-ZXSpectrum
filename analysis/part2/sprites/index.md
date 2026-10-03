# Object sprites (part 2)

First animation frame of each object type used in part 2, drawn from the part2 snapshot at 4x scale. Black is ink, white is the sprite's own paper (inside the mask), and the rest is transparent.

| Type | Name | Used as | Sprite | Image |
|------|------|---------|--------|-------|
| 01 | cube | scenery (C1) | 24x20 at FD24 | ![](type_01_cube.png) |
| 03 | (empty carried slot) | item list, location FE only | none in part 2 | - |
| 05 |  | scenery (C1) | 32x24 at FC64 | ![](type_05.png) |
| 09 | bottle | item list | 16x16 at 91D4 | ![](type_09_bottle.png) |
| 0D | skeleton | item list | 24x37 at EFA0 | ![](type_0D_skeleton.png) |
| 0E | key | item list | 16x5 at 91C0 | ![](type_0E_key.png) |
| 10 | monk | item list | 16x32 at EEA0 | ![](type_10_monk.png) |
| 12 | ogre | item list | 24x32 at E5F6 | ![](type_12_ogre.png) |
| 1A |  | scenery (C1) | invisible | - |
| 1B |  | scenery (C1) | invisible | - |
| 1C |  | scenery (C1) | invisible | - |
| 1D |  | scenery (C1) | 40x23 at F6B8 | ![](type_1D.png) |
| 20 |  | scenery (C1) | invisible | - |
| 25 | guard | item list | 24x26 at F79E | ![](type_25_guard.png) |
| 26 | bat | item list | 24x15 at EA76 | ![](type_26_bat.png) |
| 2B | potion | item list | 16x10 at 908A | ![](type_2B_potion.png) |
| 2C | table | item list | 40x34 at F508 | ![](type_2C_table.png) |
| 2D | stool | item list | 16x13 at F4D4 | ![](type_2D_stool.png) |
| 2E | spiky ball | item list | 24x16 at EDE0 | ![](type_2E_spiky_ball.png) |
| 2F | disk | item list | 24x9 at E58A | ![](type_2F_disk.png) |
| 30 | magic carpet | item list | 24x14 at E4E0 | ![](type_30_magic_carpet.png) |
| 31 | sword | item list | 16x7 at 906E | ![](type_31_sword.png) |
| 32 | book | item list | 24x14 at E536 | ![](type_32_book.png) |
| 33 | moving block | item list | 40x23 at F6B8 | ![](type_33_moving_block.png) |
| 36 |  | doorway (D5 00) | invisible | - |
| 37 |  | doorway (D5 01) | 24x51 at FD9C | ![](type_37.png) |
| 38 |  | doorway (D5 02) | invisible | - |
| 39 |  | doorway (D5 03) | 24x51 at FECE | ![](type_39.png) |

Type 03 appears in part 2 only as the placeholder for an empty carried-object slot, which is never
drawn. Its type-table entry (24x23 at EE2E) is only valid in part 1. In part 2 that memory holds
the spiky ball's animation frames (24x16, from EDE0), so there is no type 03 image here. See part
1's sprites for its real graphic.

