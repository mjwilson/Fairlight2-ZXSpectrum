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


| Opcode    | Behaviour |
| -------- | ------- |
| C1 | Insert scenery into a room.
| C3  | Sets position (typically used before including a template)    |
| CD | End-of-data marker for a template. Not actually found in the snapshot data, as it is dynamically  written into memory as required, then the previous value restored.     |
| D0    | Sets the colours for the screen.    |
| D6/D7    | Include a template. Takes a single operand, either directly or indirectly (see below). The difference between the two op-codes is that D7 preserves the state of the room-drawing code when calling the template, and restores it afterwards; D6 shares the state with the template execution. |
| DA    | Re-positions the cursor, for setting the start position of a new line. |
| DC    | Textured flood fill. Takes a single operand, either directly or indirectly. |
| E1-E6 | Flag setting or clearing. These operate on the single bits of a flag byte.   Takes a single operand, either directly or indirectly. |
| E7    | Sets up an exit to another room. Takes 5 bytes as operands: the first byte is the index of the exit (starts at 1 then increments), the next byte is the room number to exit 2, and the next 3 bytes identify the position (and perhaps the size) of the exit. |
| E9    | POKEs an address. |

## Indirect verus direct operators

Some opcodes use a mechanism of fetching the operators which allow either direct or indirect fetching of values.

For example, when including a template with 'D6', the most common way of doing this is, for example, `d6 ff 78`. The `ff` indicates a direct parameter and so template 78 will be included.

If the `ff` byte is not present, then the operand is found from a look-up table. For example, when
loading a room's data, the bytes are `d6 20`. This looks up the 0x20th entry in a look-up table starting at
C060. Each entry in the table is 2 bytes, so that entry is stored at C0A0.
Code elsewhere in the game is copied the room number to this location, so the game loads the template
corresponding to the room number.

It is not always so clear why indirect referencing is used. For example, the flag setting/clearing opcodes
typically take values 0x28 or 0x29 to clear/set the flags respectively. The benefit of having these 0/1
values in a look-up table, instead of directly in the template data, is not clear to me yet.