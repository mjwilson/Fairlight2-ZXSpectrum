# Room format

This describes the data structures of the rooms. (In fact, the format is more general, and is used for
a set of templates, of which the rooms are a subset. For example, the trees in the outside rooms are
all included into their rooms using the template structure.)

Each template is built up of a sequence of commands. These come in 2 categories.

When the first byte is less than C0, then this is a 2-byte sequence which draws a line on screen,
from the current primary cursor position to the co-ordinates represented by the 2 bytes. The
primary cursor is then updated to be this position, so that a connected sequence of lines simply
has to list a succession of end points.

When the first byte is C0 or above, it denotes an opcode described in the table below.
The meaning of all of the opcodes has not yet been decoded.

The addresses for the implementation of the opcodes are stored in a data table at 6C31 (starting with opcode C0).

| Opcode   | Address of implementation | Behaviour |
| -------- | ------- | ------- |
| c0 | 704b |
| c1 | 75f7 | Insert scenery into a room. |
| c2 | 762b | Reads a single byte operand; uses that to index a look-up table at 7A17 and initialises 6 bytes based on those values (at 9D1F, 9D33, 9D46, 9D5A, 9D70, and 9D84) - usage of these bytes is not known. |
| c3 | 7656 | Sets position (typically used before including a template) |
| c4 | 6e08 |
| c5 | 6d3f |
| c6 | 6d5f |
| c7 | 6d67 |
| c8 | 6d6b |
| c9 | 6d12 |
| ca | 754c |
| cb | 766f |
| cc | 6d63 |
| cd | 6c29 | End-of-data marker for a template. Not typically found in the snapshot data, as it is dynamically  written into memory as required, then the previous value restored. |
| ce | 6e15 |
| cf | 6e0f |
| d0 | 710a | Sets the colours for the screen. Takes a single attribute value as operand. |
| d1 | 710f | Each of D1-D4 takes a single operand and copies the byte to a specific location; exact purpose not known. |
| d2 | 7114 | Each of D1-D4 takes a single operand and copies the byte to a specific location; exact purpose not known. |
| d3 | 7119 | Each of D1-D4 takes a single operand and copies the byte to a specific location; exact purpose not known. |
| d4 | 711e | Each of D1-D4 takes a single operand and copies the byte to a specific location; exact purpose not known. |
| d5 | 75f1 | Sometimes seems to be responsible for drawing a door frame (but not always?) |
| d6 | 719d | Include a template. Takes a single operand, either directly or indirectly (see below). The difference between the two op-codes is that D7 preserves the state of the room-drawing code when calling the template, and restores it afterwards; D6 shares the state with the template execution. |
| d7 | 7148 | Include a template. Takes a single operand, either directly or indirectly (see below). The difference between the two op-codes is that D7 preserves the state of the room-drawing code when calling the template, and restores it afterwards; D6 shares the state with the template execution. |
| d8 | 70c5 |
| d9 | 70db |
| da | 6da8 |  Re-positions the cursor, for setting the start position of a new line. |
| db | 7240 |
| dc | 6e1d | Textured flood fill. Takes a single operand, either directly or indirectly. |
| dd | 7128 |
| de | 71ec |
| df | 722c |
| e0 | 7133 |
| e1 | 70e4 | Flag setting or clearing. These operate on the single bits of a flag byte held in (C024).  Takes a single operand, either directly or indirectly. See below for the meaning. |
| e2 | 70e8 | Flag setting or clearing. These operate on the single bits of a flag byte held in (C024).  Takes a single operand, either directly or indirectly. See below for the meaning. |
| e3 | 70ec | Flag setting or clearing. These operate on the single bits of a flag byte held in (C024).  Takes a single operand, either directly or indirectly. See below for the meaning. |
| e4 | 70f0 | Flag setting or clearing. These operate on the single bits of a flag byte held in (C024).  Takes a single operand, either directly or indirectly. See below for the meaning. |
| e5 | 70f4 | Flag setting or clearing. These operate on the single bits of a flag byte held in (C024).  Takes a single operand, either directly or indirectly. See below for the meaning. |
| e6 | 70f8 | Flag setting or clearing. These operate on the single bits of a flag byte held in (C024).  Takes a single operand, either directly or indirectly. See below for the meaning. |
| e7 | 75bd | Sets up an exit to another room. Takes 5 bytes as operands: the first byte is the index of the exit (starts at 1 then increments), the next byte is the room number to exit 2, and the next 3 bytes identify the position (and perhaps the size) of the exit. |
| e8 | 70bf |
| e9 | 724c | POKEs an address. Often used to mark an exit as locked. Most commonly used as `E9 FE <lo> <hi> FF <val>` to POKE val into hilo, but can also be used as `E9 FE <lo> <hi> <ix>` to look up the value to POKE from the table at C060 (see below). | 
| ea | 7256 |
| eb | 7552 |
| ec | 7139 |
| ed | 7261 |
| ee | 72cf | Purpose unclear; appears to consume bytes until a 1F termination marker. May be performing some kind of calculation |
| ef | 739d | Performs a comparison test; skips ahead a certain number of bytes in the template data if the condition is met. Decodes as EF <idx> <op> <val> <skip>; see below for the meaning of <op> |
| f0 | 73e5 |
| f1 | 752d |
| f2 | 7015 |
| f3 | 7548 |
| f4 | 7533 |
| f5 | 7537 |
| f6 | 753b |
| f7 | 73fb |
| f8 | 6d17 |
| f9 | 6cd4 |
| fa | 6d94 |
| fb | 6db4 |
| fc | 6da1 |
| fd | 7222 | Loop back to start of template |
| fe | 6cf2 |
| ff | b521 |

## E1-E6 flags

 According to ChatGPT, the flags control the room renderer:
 - Bits 0–1 select bitmap composition at $7025-$7038:
    - 00: OR / paint bits
    - 01: clear masked bits
    - 11: XOR / toggle bits
    - 10: leaves the byte unchanged on that path
- Bit 2 conditionally copies the calculated address into $C039 at $6E03.
- Bit 3 enables an auxiliary post-write path at $703B.
- Bits 4 and 6 control the coordinate/delta transform at $6DD0-$6DE2; together they choose direct, complemented, or negated handling and a base-pointer mode.
- Bit 5 calls the auxiliary routine at $704B.
- Bit 7 has no established consumer yet.

## EF operators


| byte	| meaning |
|-------|---------|
| $0D	| == |
| $0E	| >= |
| $0F	| != |
| $10	| <= |
| $11	| < |
| anything else ($12+) | >= (fallback) |


## Indirect verus direct operators

Some opcodes use a mechanism of fetching the operators which allow either direct or indirect fetching of values.

For example, when including a template with 'D6', the most common way of doing this is, for example, `d6 ff 78`. The `ff` indicates a direct parameter and so template 78 will be included.

Both `fe` and `ff` indicate a direct parameter: `ff` indicates a single-byte parameter and `fe` indicates a 16-bit word.

If the `fe`/`ff` byte is not present, then the operand is found from a look-up table. For example, when
loading a room's data, the bytes are `d6 20`. This looks up the 0x20th entry in a look-up table starting at
C060. Each entry in the table is 2 bytes, so that entry is stored at C0A0.
Code elsewhere in the game is copied the room number to this location, so the game loads the template
corresponding to the room number.

It is not always so clear why indirect referencing is used. For example, the flag setting/clearing opcodes
typically take values 0x28 or 0x29 to clear/set the flags respectively. The benefit of having these 0/1
values in a look-up table, instead of directly in the template data, is not clear to me yet.

The look-up table may be updated during gameplay (eg the room number - although it is not clear what other scenarios do this.)

In part 1, a sample check of the table looks like this:

| Table index  | Memory address | Sample value | Comments |
| ------------ | -------------- | ----- | -------- |
| 0x0          | 0xC060         | 0077  |          |
| 0x1          | 0xC062         | 0000  |          |
| 0x2          | 0xC064         | 006B  |          |
| 0x3          | 0xC066         | FCFC  | Used to store SP while calling a template include         |
| 0x4          | 0xC068         | 0000  |          |
| 0x5          | 0xC06A         | 0000  |          |
| 0x6          | 0xC06C         | 8F7E  |          |
| 0x7          | 0xC06E         | 3030  |          |
| 0x8          | 0xC070         | 3930  |          |
| 0x9          | 0xC072         | 1F39  |          |
| 0xa          | 0xC074         | 6400  |          |
| 0xb          | 0xC076         | A6A5  |          |
| 0xc          | 0xC078         | 131C  |          |
| 0xd          | 0xC07A         | 6104  |          |
| 0xe          | 0xC07C         | 0000  |          |
| 0xf          | 0xC07E         | 6101  |          |
| 0x10         | 0xC080         | 0000  |          |
| 0x11         | 0xC082         | 0000  |          |
| 0x12         | 0xC084         | 0000  |          |
| 0x13         | 0xC086         | 0000  |          |
| 0x14         | 0xC088         | 0000  |          |
| 0x15         | 0xC08A         | 0000  |          |
| 0x16         | 0xC08C         | 0000  |          |
| 0x17         | 0xC08E         | 0000  |          |
| 0x18         | 0xC090         | 0000  |          |
| 0x19         | 0xC092         | 0000  |          |
| 0x1a         | 0xC094         | 0000  |          |
| 0x1b         | 0xC096         | 0000  |          |
| 0x1c         | 0xC098         | 0000  |          |
| 0x1d         | 0xC09A         | 0000  |          |
| 0x1e         | 0xC09C         | 0000  |          |
| 0x1f         | 0xC09E         | 0000  |          |
| 0x20         | 0xC0A0         | 0002  | Holds current room number         |
| 0x21         | 0xC0A2         | 0002  |          |
| 0x22         | 0xC0A4         | 001B  |          |
| 0x23         | 0xC0A6         | 7B99  |          |
| 0x24         | 0xC0A8         | 0063  |          |
| 0x25         | 0xC0AA         | 0000  |          |
| 0x26         | 0xC0AC         | 0000  |          |
| 0x27         | 0xC0AE         | 0000  |          |
| 0x28         | 0xC0B0         | 0000  | Used to reset flags (opcodes E1-E6). Also used to choose a texture       |
| 0x29         | 0xC0B2         | 0001  | Used to set flags  (opcodes E1-E6)        |
| 0x2a         | 0xC0B4         | 0002  |          |
| 0x2b         | 0xC0B6         | 0003  | Used to choose a texture         |
| 0x2c         | 0xC0B8         | 0004  |          |
| 0x2d         | 0xC0BA         | 0005  |          |
| 0x2e         | 0xC0BC         | 9F34  |          |
| 0x2f         | 0xC0BE         | 0000  |          |
| 0x30         | 0xC0C0         | 0000  |          |
| 0x31         | 0xC0C2         | 0000  |          |
| 0x32         | 0xC0C4         | 0000  |          |
| 0x33         | 0xC0C6         | 0002  |          |
