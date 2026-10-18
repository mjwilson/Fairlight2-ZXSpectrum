# Fairlight 2, ZX Spectrum

This repo aims to document the data structures and behaviour of the ZX Spectrum
version of Fairlight 2. The original intention was to find out why the game
couldn't be completed - in fact, it was discovered that completion is possible
(although there are some bugs which make this tricky: it can't be done in the 128K
version of the game, and even in the 48K version, it can't be done if you die and restart
part 2).

Inspiration taken from https://github.com/VilleKrumlinde/FairlightZ80/tree/main

## Analysis

The analysis is done against the 48K version. Where memory addresses are specified,
these may vary beetween different editions of the game.

 * [Room format](./analysis/room_format.md)
 * [Dynamic objects](./analysis/dynamic_objects.md)
 * [Memory map](./analysis/memory_map.md)
 * [Changes in the 128K version](./analysis/128k.md)
 * [Part 1 to part 2 handover](./analysis/handover.md)

## Fixes

If you have a working 48K TZX file, you can fix the part 2 restart issues [using this tool](./fixes.html).

## AI usage

I started the analysis manually but more recently a huge amount of it has been done by Claude Code.
