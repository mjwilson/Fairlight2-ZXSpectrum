# Room format

This describes the data structures of the rooms. (In fact, the format is more general, and is used for
a set of templates, of which the rooms are a subset. For example, the trees in the outside rooms are
all included into their rooms using the template structure.)

 * [Details of templates in part 1](./part1/templates.md).
 * [Details of templates in part 2](./part2/templates.md).

Each template is built up of a sequence of commands. These come in 2 categories.

When the first byte is less than C0, the command is a 2-byte coordinate pair: `<y> <x>`. y must be
below C0 because the screen is C0 (192) lines high. That is also what separates a coordinate from
an opcode. Screen y is counted from the **bottom** of the screen, with 0 at the bottom and BF at the
top. A coordinate pair moves the pen (C037/C038) to that point, and also sets the text position
(C028). If the pen is down (flag bit 5), it draws a line from the line start (C039) to the new point.
If chaining is on (flag bit 2), the line start then follows the pen, so a connected run of lines just
lists its end points. Room templates switch both on with `d1 24`. See [Drawing flags](#drawing-flags-c024).

When the first byte is C0 or above, it denotes an opcode described in the table below.

The addresses for the implementation of the opcodes are stored in a data table at 6C31 (starting with opcode C0).

| Opcode   | Address of implementation | Behaviour |
| -------- | ------- | ------- |
| c0 | 704b | Draw a line from the line start (C039) to the pen (C037), using the current pixel mode and line pattern. |
| c1 | 75f7 | Place an object (scenery) in the room: `C1 <type> <flags> <x> <y> <z>`. Adds a 20-byte record to the room object list and draws its sprite. See [C1, D5 and CB objects](#c1-d5-and-cb-objects) below. |
| c2 | 762b | Set the room's bounding box: `C2 <n>` (a raw byte, 01-0F). It copies 6 bytes from the preset table at 7A17 + 6n into the six invisible boundary slabs at 9D18-9D8F: floor y (9D1F), ceiling y (9D33), two x walls (9D46, 9D5A) and two z walls (9D70, 9D84). The collision code (8B7E) uses these slabs. For example, preset 01 is floor 32, ceiling B4, x walls B2/28 and z walls 28/AE. |
| c3 | 7656 | Sets position (typically used before including a template) |
| c4 | 6e08 | Set the line start (C039) to the pen position (C037). |
| c5 | 6d3f | Clear the current window: zero its pixels and set its attributes. |
| c6 | 6d5f | Set the attributes of the current window to the colour from `D0` (the whole attribute byte). |
| c7 | 6d67 | Like C6, but changes only the INK bits (0-2) of the current window's attributes. |
| c8 | 6d6b | Like C6, but changes only the BRIGHT bit (6). |
| c9 | 6d12 | Tape save: `C9 <start> <length>`, through the ROM saving routine (04C6). Both parts use `c9 fe 00 40 fe 40 b7` (save 4000-F73F) for the **in-game save**. Press Space + Symbol Shift for the quit menu, then **S**: part 1 template 4D includes 70, and part 2 template 68 includes 85. A saved game is a plain memory image that carries on from just after the save when loaded. The part 2 tape image is one of these saves, made by the handover template 88 (which also includes 85). See [objects.md](objects.md#part-1-to-part-2-handover). |
| ca | 754c | Mirror the current window left to right (pixels and attributes). Uses the window-copy routine at 6A2F in mode 8. |
| cb | 766f | Place the current room's movable objects (items and creatures). No operands. Resets the six creature hit counters at 7B88-7B8D to 4, then places every entry in the item list at (C05B) whose location equals the current room in C05D. See [dynamic_objects.md](dynamic_objects.md#item-list-entries). Used once, in the main room-drawing template at DA2A, straight after the room template (`d6 20`) and `c3 00 00 00`. |
| cc | 6d63 | Like C6, but changes only the PAPER bits (3-5). |
| cd | 6c29 | End-of-data marker for a template. When D6 or D7 runs template n, it writes CD over the first byte of template n+1, and restores that byte afterwards. The marker's address is kept in C000 and the original byte in C00D. Only the innermost running template has its marker in place. In the part 1 snapshot, the marker is at D9C3 (the start of template 6C), whose real byte is E9. CD is also used directly in templates as an early return. |
| ce | 6e15 | Decrement a variable: `CE <var>`. |
| cf | 6e0f | Increment a variable: `CF <var>`. |
| d0 | 710a | Sets the colours for the screen. Takes a single attribute value as operand. |
| d1 | 710f | Set a byte directly: `D1 <n>` (literal, no FE/FF prefix) writes n to C024, which is the drawing-flags byte that E1-E6 change one bit at a time. |
| d2 | 7114 | Set a byte directly: `D2 <n>` (literal, no FE/FF prefix) writes n to C023, which is a second drawing-flags byte, which the sprite blitter at 67CD reads (bits 0, 3 and 4). |
| d3 | 7119 | Set the line pattern: `D3 <n>` writes n to C026. It is rotated once per plotted pixel, and a pixel is skipped when a 1 bit comes out, so 00 is a solid line. |
| d4 | 711e | Set the attribute mask: `D4 <n>` writes n to C027. When flag bit 3 is set, plotting a pixel also colours its attribute cell: new = (old AND C027) OR (C022 AND NOT C027). |
| d5 | 75f1 | Place a doorway/exit volume: `D5 <type> <x> <y> <z>`. Same code as C1 but uses object types 36+`type`, has no flags operand (kind is forced to 1 = exit), and only types 1 and 3 have a sprite (the visible door frames). See [C1, D5 and CB objects](#c1-d5-and-cb-objects) below. |
| d6 | 719d | Include a template. Takes a single operand, either directly or indirectly (see below). The difference between the two op-codes is that D7 preserves the state of the room-drawing code when calling the template, and restores it afterwards; D6 shares the state with the template execution. |
| d7 | 7148 | Include a template. Takes a single operand, either directly or indirectly (see below). The difference between the two op-codes is that D7 preserves the state of the room-drawing code when calling the template, and restores it afterwards; D6 shares the state with the template execution. |
| d8 | 70c5 | Call machine code: `D8 <addr>`, e.g. `d8 fe f2 7b`. IY is set to 5C3A (the ROM value) during the call. The main loop uses it to run one tick of the game engine (7BF2, which jumps to 8915). |
| d9 | 70db | Set the font: `D9 <addr>`, where addr is the address of the glyph for character 20 (space). It stores addr - 100 in C02D, so that character c is at C02D + 8c. The character advance is C02C, which is set with a POKE, e.g. `e9 fe 2c c0 ff 05` gives 5 pixels. |
| da | 6da8 | Move the line start: `DA <y> <x>` (raw bytes). This is like a plain coordinate pair, but it sets C039 (the line start) instead of the pen, and never draws. If flag bit 4 is set, it is relative to the current line start. |
| db | 7240 | POKE a 16-bit word: `DB <addr> <value>`. Both are ordinary operands. For example, `db fe 58 c0 2e` sets the word at C058 to var2E. See E9 for the byte version. |
| dc | 6e1d | Textured flood fill. Takes a single operand, either directly or indirectly. |
| dd | 7128 | Set the border colour: `DD <colour>` (OUT FE, bits 0-2; also kept in C021). |
| de | 71ec | Select window `n`: `DE <n>`. Copies the 5-byte definition of window n (from C037 + 5n) into the current-window variables at C032-C036. The window also sets where text is printed. |
| df | 722c | Pause: `DF <n>`. Waits about n × 1024 × 4 empty loop iterations. `DF 0` (or a value that evaluates to 0) waits for a key press instead. |
| e0 | 7133 | Print a number in decimal, without leading zeros: `E0 <value>`. |
| e1 | 70e4 | Set or clear flag bit 10 of C024 (relative coordinates): `E1 <v>`. The bit is set if bit 0 of v is 1 (usually var29) and cleared if it is 0 (usually var28). See [Drawing flags](#drawing-flags-c024). |
| e2 | 70e8 | Set or clear flag bit 04 of C024 (chain lines): `E2 <v>`. The bit is set if bit 0 of v is 1 (usually var29) and cleared if it is 0 (usually var28). See [Drawing flags](#drawing-flags-c024). |
| e3 | 70ec | Set or clear flag bit 02 of C024 (erase mode): `E3 <v>`. The bit is set if bit 0 of v is 1 (usually var29) and cleared if it is 0 (usually var28). See [Drawing flags](#drawing-flags-c024). |
| e4 | 70f0 | Set or clear flag bit 20 of C024 (pen down): `E4 <v>`. The bit is set if bit 0 of v is 1 (usually var29) and cleared if it is 0 (usually var28). See [Drawing flags](#drawing-flags-c024). |
| e5 | 70f4 | Set or clear flag bit 40 of C024 (mirror x): `E5 <v>`. The bit is set if bit 0 of v is 1 (usually var29) and cleared if it is 0 (usually var28). See [Drawing flags](#drawing-flags-c024). |
| e6 | 70f8 | Set or clear flag bit 01 of C024 (XOR mode): `E6 <v>`. The bit is set if bit 0 of v is 1 (usually var29) and cleared if it is 0 (usually var28). See [Drawing flags](#drawing-flags-c024). |
| e7 | 75bd | Sets up an exit to another room: `E7 <n> <room> <x> <y> <z>`. Finds the n-th object in the room whose kind (record byte 12, low nibble) is 1 - i.e. normally the n-th `D5` doorway placed so far - and writes `<room>` and the 3 position bytes into record bytes 14-17. The position is presumably where the player appears in the destination room. |
| e8 | 70bf | Print one character: `E8 <char>`. |
| e9 | 724c | POKEs an address. Often used to mark an exit as locked. Most commonly used as `E9 FE <lo> <hi> FF <val>` to POKE val into hilo, but can also be used as `E9 FE <lo> <hi> <ix>` to look up the value to POKE from the table at C060 (see below). | 
| ea | 7256 | OUT to a port: `EA <port> <value>`. |
| eb | 7552 | Copy window a to window b: `EB <a> <b>` (pixels and attributes). Uses 6A2F in mode 1. |
| ec | 7139 | Print inline text: `EC <len> <text...>`. The instruction is 1 + len bytes long, and the text ends with 1F. It can contain control codes. See [Text](#text). |
| ed | 7261 | Define window `n`: `ED <n> <x> <y> <w> <h> <e>`. It is stored as 5 bytes at C037 + 5n, and `DE` copies it into C032-C036. x is the left edge (rounded down to a multiple of 8), y is the top line (7 ORed in, counted from the bottom), and w and h are the width and height in character cells, trimmed so the window fits. e is added to the high byte of every screen address, so it picks the screen the window draws on: 00 is the real screen at 4000, 61 is the off-screen buffer at A100. |
| ee | 72cf | Evaluate an expression and store the result in a C060 variable: `EE <len> <dest> <expression...> 1F`. See [EE expressions](#ee-expressions) below. |
| ef | 739d | Performs a comparison test; skips ahead a certain number of bytes in the template data if the condition is met. Decodes as EF <idx> <op> <val> <skip>; see below for the meaning of <op> |
| f0 | 73e5 | Draw a sprite at the line start (C039): `F0 <address> <width> <height>` (width in pixels, height in lines). Uses the blitter at 67CD. |
| f1 | 752d | Invert the current window's pixels (6A2F in mode 4, with CPL patched in at 6A82). |
| f2 | 7015 | Plot a single point at the pen position (C037). |
| f3 | 7548 | Swap the contents of windows a and b: `F3 <a> <b>` (6A2F in mode 2). |
| f4 | 7533 | Combine window a into window b with XOR: `F4 <a> <b>` (pixels only; mode 4 with XOR (HL) patched in at 6A82). |
| f5 | 7537 | As F4, but with AND. |
| f6 | 753b | As F4, but with OR. |
| f7 | 73fb | Scroll the current window vertically: `F7 <n>`. Bits 0-2 + 1 give the distance in pixels (1-8). Bit 5 set scrolls up, clear scrolls down. Bit 3 set also scrolls the attributes. Bit 4 set wraps the content round (through the buffer at B900). Bit 7 set leaves the uncovered lines uncleared (otherwise they are cleared to 0). The main loop uses `f7 ff 67` to scroll the message window. |
| f8 | 6d17 | Tape load: `F8 <start> <length>`, through the ROM loading routine (0562). `f8 fe 00 40 fe 40 b7` (load 4000-F73F) is the **in-game load** (quit menu, then **L**: part 1 template 6F, part 2 template 84). Part 1 uses the same template 6F to load part 2 at the end of the game (template 95). Part 2 also has `f8 fe 00 a1 fe b8 0b` (template 8F, the A100 code block) and `f8 fe 00 40 fe 00 1b` (template 86, the screen only), which nothing includes. |
| f9 | 6cd4 | Beep: `F9 <duration> <pitch>`, through ROM BEEPER (03B5) with DE = duration and HL = pitch. |
| fa | 6d94 | Set the origin for absolute coordinates: `FA <x> <y>` (stored in C062/C063). Used when flag bit 4 is clear. |
| fb | 6db4 | Like a plain coordinate pair (move the pen, and draw if the pen is down), but y and x are standard operands (`FB <y> <x>`). |
| fc | 6da1 | Like `DA`, but y and x are standard operands (`FC <y> <x>`). |
| fd | 7222 | Loop back to the start of the current template (from C010). It also checks the BREAK keys (6C07). |
| fe | 6cf2 | Block copy: `FE <dest> <src> <len>`. Handles overlapping blocks correctly (LDIR or LDDR). Note that FE is also the word-operand prefix, so the meaning depends on position: in the opcode position it is this opcode. |
| ff | b521 | Not used. The table entry points to B521, which is data, not code. |

## Indirect versus direct operators

Some opcodes use a mechanism of fetching the operators which allow either direct or indirect fetching of values.

For example, when including a template with 'D6', the most common way of doing this is, for example, `d6 ff 78`. The `ff` indicates a direct parameter and so template 78 will be included (this example is from part 1's template 02).

Both `fe` and `ff` indicate a direct parameter: `ff` indicates a single-byte parameter and `fe` indicates a 16-bit word.

If the `fe`/`ff` byte is not present, then the operand is found from a look-up table. For example, when
loading a room's data, the bytes are `d6 20`. This looks up the 0x20th entry in a look-up table starting at
C060. Each entry in the table is 2 bytes, so that entry is stored at C0A0.
Code elsewhere in the game copies the room number to this location, so the game loads the template
corresponding to the room number.

### How the table is divided

The table falls into two halves.

- **Entries 00-1F (C060-C09F) are not really script variables.** This memory is also the
  renderer's working storage, which the line-drawing and fill code (6600-7050) writes constantly.
  The interpreter's own state lives here too: C064 is a saved SP, and C066 is used by D7. None of
  the templates I checked uses an index below 20.
- **Entries from 20 upwards are the script variables.** They run from C0A0 up to the start of the
  template table, whose address is held in C008, so the number of variables differs between the
  parts. In part 1, C008 = C0C8, giving entries 20-33 (C0A0-C0C7). In part 2, C008 = C0DC,
  giving entries 20-3D (C0A0-C0DB). Part 2 uses the extra entries for more constants (35-3A) and
  for var3C, the room 50 lock. No machine code writes to them directly. They change only through
  `EE` (and `CE`/`CF`) in the templates.
  The one exception is `D7`: it copies C0A0 up to (C008) onto the stack, together with C01E-C067,
  and restores them when the included template returns. Any variable changes made inside a
  D7-included template are therefore undone. D6 includes share the variables.

#### Variable names

Template 00 is never run by the game. It holds the names of the script variables, from var20
upwards, as a list of `EC` text strings. It was probably left behind by the authors' development
tools. The names match what the variables are used for:

| Var | Part 1 | Part 2 | Use |
|-----|--------|--------|-----|
| 20-23 | A, B, C, D | A, B, C, D | 20 is the current room, 21 the room the player is in; 22 and 23 are temporaries |
| 24 | LIFE | LIFE | Energy, and other values being tested |
| 25-27 | X, Y, Z | X, Y, Z | |
| 28-2D | N0-N5 | N0-N5 | The constants 0-5 |
| 2E, 2F | E, F | E, F | Temporaries |
| 30-32 | X1, Y1, Z1 | X1, Y1, Z1 | |
| 33 | ROOM | A1 | Part 1's start room |
| 34 | - | ROOM | Part 2's start room |
| 35-3A | - | N15, N6, N7, N8, N9, N13 | Part 2's extra constants (0F, 6, 7, 8, 9, 0D) |
| 3B | - | AA | The "handover not done yet" flag (999 at power-on) |
| 3C | - | KEY | The lock on the room 50 door (the magic wand) |
| 3D | - | (no name) | |

## C1, D5 and CB objects

`C1` (handler 75F7) and `D5` (handler 75F1) share the same code (75FB, subroutine 76AE). The only
difference is bit 0 of C07D, which D5 sets and C1 clears.

```
C1 <type> <flags> <x> <y> <z>      ; 6 bytes - every C1 in part 1 has this length
D5 <type> <x> <y> <z>              ; 5 bytes
```

All operands are plain bytes (no FE/FF direct/indirect prefix).

- `<type>` indexes an 11-byte object-type table at 7768 (entry address = 7768 + 11*type).
  C1 uses entries 00-35; D5 adds 36, so it uses entries 36-3E.
- `<flags>` (C1 only) is stored unchanged in byte 12 of the object record. D5 always stores 01 there.
  The low nibble is the object "kind" and the high bits are behaviour flags (see [dynamic_objects.md](dynamic_objects.md#kind-and-flags-record-byte-12)).
- `<x> <y> <z>` are offsets from the current `C3` position (C055/C056/C057), not absolute
  coordinates. The handler adds them at 7700, using 8-bit arithmetic that wraps. This lets a
  template place the same objects anywhere. For example, part 1's template 61 contains
  `c1 00 00 32 62 32`. It is included after `c3 3c 00 32` in one room, which places the object at
  (6E,62,64), and after `c3 1e 00 5a` in another, which places it at (50,62,8C). The C3 position
  stays in effect after a `D6` include returns. Room templates that use absolute coordinates
  therefore reset it first with `c3 00 00 00`, as the main room template does before `CB`. World
  y increases upwards, and an object's y is its top. It occupies y − ysize up to y, and the floor
  is at 32. For example, the doors in part 1's template 02 are at y=6E with ysize 3C, the player is at 4E
  with ysize 1C, and type 13 is at 4C with ysize 1A. All three stand on the floor at 32.

`CB` has no operands. It places the room's movable objects (items and creatures) from a separate
item list, using the same routine as C1.

CB also adds the C3 position to the positions in the list. That is why the main room template
(DA2A) runs `c3 00 00 00` just before `cb`.

The object-type table, the object record layout, the meaning of the flags, the item list, and the
game logic for picking up objects and fighting are described in [objects.md](objects.md).

## Drawing flags (C024)

C024 is set as a whole by `D1`, or one bit at a time by E1-E6. It starts at 00 (6B96). The meanings
below are checked against the code (6DCD-6E07 for coordinates, 7025-7046 for plotting).

| Bit | Set by | Meaning |
|-----|--------|---------|
| 0 (01) | E6 | XOR: the pixel is toggled (7032). Also used by text control codes 1D and 1E. |
| 1 (02) | E3 | Erase, when bit 0 is clear: the pixel is ORed and then toggled, which clears it (702C). Also used by text control codes 04 and 05. |
| 2 (04) | E2 | Chain: after drawing, the line start (C039) moves to the pen (6E03). |
| 3 (08) | D1 only | Colour: each plotted pixel also sets its attribute cell from C022, through the mask C027 (675F). Also used by text control codes 18 and 19. |
| 4 (10) | E1 | Relative: coordinates are added to the current position. When clear, they are added to the origin set by `FA` (C062/C063). |
| 5 (20) | E4 | Pen down: a coordinate pair draws a line from the line start to the new point (704B). |
| 6 (40) | E5 | Mirror x: the x value is complemented (absolute mode) or negated (relative mode). This lets one template draw a left-right mirrored copy. |
| 7 (80) | - | Not used by the drawing code. |

If bits 0 and 1 are both clear, the pixel is ORed (painted).

## Windows

Drawing, clearing, scrolling and text all work inside the **current window**, whose definition is
held in C032-C036. There are five numbered windows. `ED n ...` defines window n, and `DE n` copies
it into the current-window variables.

Window n is stored as 5 bytes at C037 + 5n, so windows 1-5 occupy C03C-C054. There is no window 0,
because that address is the pen position (C037). There is no window 6 either: the C3 position
starts straight after, at C055. The 5 bytes are:

| Byte | Meaning |
|------|---------|
| 0 | Left edge x (a multiple of 8) |
| 1 | Top line y, counted from the bottom (7 ORed in) |
| 2 | Width in character cells |
| 3 | Height in character cells |
| 4 | Screen offset, added to the high byte of every screen address: 00 is the real screen at 4000, 61 is the off-screen buffer at A100 |

`DE` also works out the right edge and bottom line, and stores them in C031 and C030.

How the game uses them (part 1 template numbers, part 2 in brackets):

| Window | Defined by | Area | Screen | Used for |
|--------|------------|------|--------|----------|
| 1 | Start-up defaults (6B96) | Whole screen, 32x24 cells | Real (00) | General drawing and text. Selected with `de 29` (var29 = 1). |
| 2 | Start-up defaults (6B96) | Whole screen, 32x24 cells | Off-screen buffer (61) | Clearing the buffer and drawing the new room off-screen (`de 2a` in 6C [77]) |
| 3 | `ed 2b ...` in 6A [83] | Play area: x = 10, top line A7, 28x19 cells | Real (00) | Where the game is shown. The main loop selects it before each engine tick. |
| 4 | `ed 2c ...` in 69 [75] | The same play area | Off-screen buffer (61) | The room drawn off-screen |
| 5 | Redefined as needed | Varies | Real (00) | A scratch window. The main loop uses it as the message box: `ed 2d ff 08 ff b7 ff 09 2a 28`, 9x2 cells at x = 08, top line B7, which `f7 ff 67` scrolls up a line at a time. The inventory and status displays also use it (template 56 in part 1, 6F in part 2). |

6A [83] also defines window 3 briefly as a strip at the top of the screen (x = 60, 14x3 cells)
while it draws the status panel, then sets it back to the play area.

Pairing the windows makes room drawing flicker-free. The room-entry template selects window 2,
clears it and draws the room into the buffer. It then copies the buffer's play area onto the
visible one in one go with `eb ff 04 ff 03` (copy window 4 to window 3).

## Text

`EC`, `E8` and `E0` print using the font set by `D9` (address in C02D, advance in C02C), at the
text position C028. Coordinate pairs also update the text position. Text passed to EC ends with 1F.
Codes below 20 are control codes (handled at 669A-675E).

## EE expressions

```
EE <len> <dest> <term> [<op> <term>]... 1F
```

EE works out a 16-bit value from left to right and stores it in variable `<dest>`, which is
entry `<dest>` of the C060 table. It is the scripting language's assignment statement.

- `<len>` is the number of bytes that follow it, up to and including the 1F. The handler ignores
  it. Presumably other code uses it to skip over the instruction.
- `<dest>` is a variable index (always indirect, never FE/FF).
- `<term>` is one of:
  - an ordinary operand: a variable index, `FF nn` (a byte), or `FE lo hi` (a word);
  - `0A <operand>`: read the 16-bit word at that address;
  - `0B <operand>`: read the byte at that address;
  - `09 <port> <high>`: `IN` from a port (`<high>` is the top byte of the port address). Used to
    read the keyboard;
  - `08`: a keyboard read through the ROM (679A). This is less certain.
- `<op>` is 01 add, 02 subtract, 03 multiply, 04 divide, 05 AND, 06 OR, or 07 XOR. If it is left
  out, add is assumed, so the first term simply loads the running total, which starts at 0.
- `1F` ends the expression and stores the result.

The handler is at 72CF. The token dispatch is at 72FD, and the table at 7310 is indexed by the
op or token byte.

Examples:
- `ee 07 22 0b fe 70 7b 1f` sets var22 to the byte at 7B70.
- `ee 07 24 0b fe 85 7b 1f` sets var24 to the byte at 7B85, the player's energy.
- `ee 0a 22 0b fe 77 7b 01 ff 50 1f` sets var22 to the byte at 7B77 plus 50.
- `ee 0e 22 09 ff fe ff fd 05 ff 1f` sets var22 to `IN (FDFE) AND 1F`, one keyboard row.
- `ee 07 23 23 01 ff 20 1f` sets var23 to var23 plus 20.

## EF operators


| byte	| meaning |
|-------|---------|
| $0D	| == |
| $0E	| >= |
| $0F	| != |
| $10	| <= |
| $11	| < |
| anything else ($12+) | > (checked at 73D9: skips only if the first value is strictly greater) |
