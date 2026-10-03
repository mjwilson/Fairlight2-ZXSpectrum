| Template index  | Comments |
| ------------ | -------- |
| 0x02 ... 0x4a          | Regular rooms          |
| 0x4a | 'falling off a cliff' |
| 0x4b | ship's mast |
| 0x4e | beach room with irregular edges |
| 0x51 | |
| 0x52 | included from template 0x51 |
| 0x54 | included from template 0x69 |
| 0x55 | | 
| 0x56 | included from template 0x69  |
| 0x57 | included from template 0x56 |
| 0x58 |  |
| 0x59 |  |
| 0x5a | included from template 0x6c |
| 0x5b | included from template 0x5a |
| 0x5c | included from template 0x4f, 0x56 |
| 0x5d | triple shrubbery | 
| 0x5e | another double shrubbery? |
| 0x5f | see room 0x2b |
| 0x60 | big tree |
| 0x61 | very big tree |
| 0x62 | other big tree |
| 0x63 | small tree |
| 0x65 | 5x shrubbery |
| 0x66 | porthole on ship |
| 0x76 | castle door |
| 0x78 | outdoor square room with castle wall |
| 0x79 | outdoor empty square room; no floor fill |
| 0x7a | outdoor square room |
| 0x7b | outdoor square room by cliff edge |
| 0x80 | castle door |
| 0x87 | window |
| 0x89 | indoor rectangular room |
| 0x8a | see room $25 |
| 0x8b | indoor narrow rectangular room |
| 0x8d | see room $32, $38 |
| 0x8e | see room $35, $36, $37 |
| 0x8f | see room $44, $47 |
| 0x92 | octagonal room |

```
TEMPLATE 02
c270: e5 29 ; flag 40: mirror x
c272: 5c c8 ; pen to (y, x)
c274: d7 ff 7d ; include template (save/restore state)
c277: e5 28 ; flag 40: mirror x
c279: d6 ff 78 ; include template
c27c: 64 32 ; pen to (y, x)
c27e: dc 2b ; textured flood fill
c280: e7 01 03 36 6e 32 ; room exit
c286: e7 02 07 32 6e ac ; room exit
c28c: e9 fe de 9d ff ff ; POKE byte
c292: c1 13 00 a6 4c a6 ; place object (type, flags, x, y, z)
c298: c3 00 00 6e ; set object position
c29c: d6 ff 63 ; include template
c29f: c3 3a 00 6e ; set object position
c2a3: d6 ff 63 ; include template
c2a6: c3 3c 00 32 ; set object position
c2aa: d6 ff 61 ; include template

TEMPLATE 03
c2ad: d6 ff 78 ; include template
c2b0: e7 01 04 36 6e 32 ; room exit
c2b6: e7 02 08 32 6e ac ; room exit
c2bc: e7 03 02 ae 6e 32 ; room exit
c2c2: c3 0a 00 0a ; set object position
c2c6: d6 ff 60 ; include template
c2c9: c3 1e 00 5a ; set object position
c2cd: d6 ff 61 ; include template
c2d0: c3 00 00 00 ; set object position
c2d4: c1 13 00 32 4c a6 ; place object (type, flags, x, y, z)
c2da: c1 13 00 40 4c a6 ; place object (type, flags, x, y, z)
c2e0: c1 13 00 4e 4c a6 ; place object (type, flags, x, y, z)

TEMPLATE 04
c2e6: d6 ff 78 ; include template
c2e9: e7 01 05 36 6e 32 ; room exit
c2ef: e7 02 09 32 6e ac ; room exit
c2f5: e7 03 03 ae 6e 32 ; room exit
c2fb: d6 ff 5d ; include template
c2fe: c3 ec 00 f0 ; set object position
c302: d6 ff 5d ; include template

TEMPLATE 05
c305: d6 ff 4e ; include template
c308: e7 03 0a 32 6e ac ; room exit
c30e: e7 04 04 ae 6e 32 ; room exit

TEMPLATE 06
c314: c5 ; clear window
c315: d0 28 ; set attribute
c317: d1 24 ; set drawing flags (C024)
c319: da 40 ff ; move line start
c31c: 00 80 ; pen to (y, x)
c31e: da 5b 51 ; move line start
c321: 6c 74 ; pen to (y, x)
c323: 40 ff ; pen to (y, x)
c325: da 5b 51 ; move line start
c328: 43 51 ; pen to (y, x)
c32a: 00 6d ; pen to (y, x)
c32c: da 30 59 ; move line start
c32f: 00 60 ; pen to (y, x)
c331: da 27 5d ; move line start
c334: 00 63 ; pen to (y, x)
c336: da 5c 51 ; move line start
c339: 6d 51 ; pen to (y, x)
c33b: 7e 73 ; pen to (y, x)
c33d: 6c 73 ; pen to (y, x)
c33f: 7e 73 ; pen to (y, x)
c341: 56 ff ; pen to (y, x)
c343: da 4e 51 ; move line start
c346: 53 4f ; pen to (y, x)
c348: 6e 4f ; pen to (y, x)
c34a: 80 72 ; pen to (y, x)
c34c: 58 ff ; pen to (y, x)
c34e: 40 ff ; pen to (y, x)
c350: 41 fc ; pen to (y, x)
c352: 51 fc ; pen to (y, x)
c354: 75 80 ; pen to (y, x)
c356: 6c 77 ; pen to (y, x)
c358: 74 82 ; pen to (y, x)
c35a: 6c 7a ; pen to (y, x)
c35c: 43 fb ; pen to (y, x)
c35e: da 6a 71 ; move line start
c361: 79 71 ; pen to (y, x)
c363: 6b 70 ; pen to (y, x)
c365: 78 70 ; pen to (y, x)
c367: 6a 53 ; pen to (y, x)
c369: 5b 53 ; pen to (y, x)
c36b: da 73 57 ; move line start
c36e: ba 10 ; pen to (y, x)
c370: b9 0d ; pen to (y, x)
c372: b1 0d ; pen to (y, x)
c374: 6f 4f ; pen to (y, x)
c376: da 71 54 ; move line start
c379: b8 0d ; pen to (y, x)
c37b: af 16 ; pen to (y, x)
c37d: a7 16 ; pen to (y, x)
c37f: b1 19 ; pen to (y, x)
c381: bf 36 ; pen to (y, x)
c383: d1 00 ; set drawing flags (C024)
c385: 58 69 ; pen to (y, x)
c387: dc ff 11 ; textured flood fill
c38a: 51 54 ; pen to (y, x)
c38c: dc ff 0e ; textured flood fill
c38f: 66 64 ; pen to (y, x)
c391: dc ff 0e ; textured flood fill
c394: 67 8d ; pen to (y, x)
c396: dc ff 0b ; textured flood fill
c399: 77 88 ; pen to (y, x)
c39b: dc 28 ; textured flood fill
c39d: c2 09 ; set room bounding box (preset)
c39f: c1 1a 00 5c 46 8c ; place object (type, flags, x, y, z)
c3a5: c1 1a 00 48 46 74 ; place object (type, flags, x, y, z)
c3ab: c1 1a 00 34 46 4e ; place object (type, flags, x, y, z)
c3b1: c1 1a 00 9c 46 7c ; place object (type, flags, x, y, z)
c3b7: d5 05 3c 6e 32 ; place doorway (type, x, y, z)
c3bc: e7 01 0e 3c 6e ac ; room exit

TEMPLATE 07
c3c2: d6 ff 7b ; include template
c3c5: e7 01 02 32 6e 36 ; room exit
c3cb: e7 02 08 36 6e 32 ; room exit
c3d1: e7 03 0f 32 6e ac ; room exit
c3d7: e7 04 4a 64 a0 32 ; room exit
c3dd: c3 c8 00 e6 ; set object position
c3e1: d6 ff 5d ; include template
c3e4: c3 1e 00 46 ; set object position
c3e8: d6 ff 60 ; include template
c3eb: c3 1a 00 28 ; set object position
c3ef: d6 ff 60 ; include template
c3f2: c3 3c 00 28 ; set object position
c3f6: d6 ff 61 ; include template

TEMPLATE 08
c3f9: d7 ff 7a ; include template (save/restore state)
c3fc: e7 01 03 32 6e 36 ; room exit
c402: e7 02 09 36 6e 32 ; room exit
c408: e7 03 10 32 6e ac ; room exit
c40e: e7 04 07 ac 6e 32 ; room exit
c414: c3 3c 00 32 ; set object position
c418: d6 ff 61 ; include template
c41b: c3 1e 00 46 ; set object position
c41f: d6 ff 60 ; include template
c422: c3 28 00 0c ; set object position
c426: d6 ff 61 ; include template
c429: c3 0c 00 0c ; set object position
c42d: d6 ff 62 ; include template

TEMPLATE 09
c430: d6 ff 7a ; include template
c433: e7 01 04 32 6e 36 ; room exit
c439: e7 02 0a 36 6e 32 ; room exit
c43f: e7 03 11 32 6e ac ; room exit
c445: e7 04 08 ac 6e 32 ; room exit
c44b: d6 ff 5e ; include template
c44e: c3 46 00 3c ; set object position
c452: d6 ff 62 ; include template

TEMPLATE 0a
c455: d6 ff 7a ; include template
c458: e7 01 05 32 6e 36 ; room exit
c45e: e7 02 0b 36 6e 32 ; room exit
c464: e7 03 12 32 6e ac ; room exit
c46a: e7 04 09 ac 6e 32 ; room exit
c470: c3 3c 00 32 ; set object position
c474: d6 ff 61 ; include template
c477: c3 14 00 50 ; set object position
c47b: d6 ff 62 ; include template
c47e: c3 28 00 0c ; set object position
c482: d6 ff 61 ; include template
c485: c3 0c 00 0c ; set object position
c489: d6 ff 62 ; include template

TEMPLATE 0b
c48c: d6 ff 4e ; include template
c48f: e7 03 13 32 6e ac ; room exit
c495: e7 04 0a ae 6e 32 ; room exit

TEMPLATE 0c
c49b: d0 28 ; set attribute
c49d: e4 29 ; flag 20: pen down
c49f: e2 29 ; flag 04: chain lines
c4a1: da 40 ff ; move line start
c4a4: 00 80 ; pen to (y, x)
c4a6: 40 00 ; pen to (y, x)
c4a8: 80 80 ; pen to (y, x)
c4aa: 40 ff ; pen to (y, x)
c4ac: 54 af ; pen to (y, x)
c4ae: 59 8a ; pen to (y, x)
c4b0: 56 5d ; pen to (y, x)
c4b2: 50 43 ; pen to (y, x)
c4b4: 3f 2e ; pen to (y, x)
c4b6: 2e 27 ; pen to (y, x)
c4b8: 1e 58 ; pen to (y, x)
c4ba: 0d 7f ; pen to (y, x)
c4bc: 0d 7f ; pen to (y, x)
c4be: 0d 7f ; pen to (y, x)
c4c0: 33 d7 ; pen to (y, x)
c4c2: 3e fc ; pen to (y, x)
c4c4: e4 28 ; flag 20: pen down
c4c6: e2 28 ; flag 04: chain lines
c4c8: 03 80 ; pen to (y, x)
c4ca: dc 2b ; textured flood fill
c4cc: 3c 64 ; pen to (y, x)
c4ce: dc 29 ; textured flood fill
c4d0: c2 01 ; set room bounding box (preset)
c4d2: d5 05 00 72 32 ; place doorway (type, x, y, z)
c4d7: d5 04 b2 6e 32 ; place doorway (type, x, y, z)
c4dc: c1 1b 02 32 34 32 ; place object (type, flags, x, y, z)
c4e2: c1 1b 02 32 36 58 ; place object (type, flags, x, y, z)
c4e8: c1 1b 03 36 34 30 ; place object (type, flags, x, y, z)
c4ee: c1 1b 03 12 36 24 ; place object (type, flags, x, y, z)
c4f4: e7 01 14 0a 6e ac ; room exit
c4fa: e7 02 0d 36 6e 58 ; room exit
c500: c1 1d 00 9e 36 46 ; place object (type, flags, x, y, z)
c506: c1 1d 00 8a 36 46 ; place object (type, flags, x, y, z)
c50c: c1 1d 00 76 36 46 ; place object (type, flags, x, y, z)
c512: e9 fe 24 9d ff 07 ; POKE byte

TEMPLATE 0d
c518: d0 28 ; set attribute
c51a: d6 ff 79 ; include template
c51d: c1 1d 00 9a 36 6c ; place object (type, flags, x, y, z)
c523: c1 1d 00 86 36 6c ; place object (type, flags, x, y, z)
c529: c1 1d 00 72 36 6c ; place object (type, flags, x, y, z)
c52f: c1 1d 00 5e 36 6c ; place object (type, flags, x, y, z)
c535: c1 1d 00 4a 36 6c ; place object (type, flags, x, y, z)
c53b: c1 1d 00 36 36 6c ; place object (type, flags, x, y, z)
c541: e7 02 0e 36 74 1e ; room exit
c547: e7 04 0c ae 6e 0c ; room exit
c54d: e9 fe 24 9d ff 07 ; POKE byte

TEMPLATE 0e
c553: d0 28 ; set attribute
c555: d1 00 ; set drawing flags (C024)
c557: 73 69 ; pen to (y, x)
c559: d1 24 ; set drawing flags (C024)
c55b: da 40 ff ; move line start
c55e: 00 80 ; pen to (y, x)
c560: 14 4e ; pen to (y, x)
c562: 2e 2b ; pen to (y, x)
c564: 48 11 ; pen to (y, x)
c566: 7a 74 ; pen to (y, x)
c568: 71 9d ; pen to (y, x)
c56a: 5b d4 ; pen to (y, x)
c56c: 40 ff ; pen to (y, x)
c56e: 54 ff ; pen to (y, x)
c570: 6b d9 ; pen to (y, x)
c572: 81 a0 ; pen to (y, x)
c574: 86 89 ; pen to (y, x)
c576: 89 7d ; pen to (y, x)
c578: 8a 76 ; pen to (y, x)
c57a: 7b 76 ; pen to (y, x)
c57c: 8d 76 ; pen to (y, x)
c57e: 88 8a ; pen to (y, x)
c580: 83 a2 ; pen to (y, x)
c582: 6f d6 ; pen to (y, x)
c584: 57 ff ; pen to (y, x)
c586: d1 00 ; set drawing flags (C024)
c588: 7c 89 ; pen to (y, x)
c58a: d6 ff 66 ; include template
c58d: d1 00 ; set drawing flags (C024)
c58f: 75 a3 ; pen to (y, x)
c591: d6 ff 66 ; include template
c594: d1 00 ; set drawing flags (C024)
c596: 68 c4 ; pen to (y, x)
c598: d6 ff 66 ; include template
c59b: d1 00 ; set drawing flags (C024)
c59d: 58 e2 ; pen to (y, x)
c59f: d6 ff 66 ; include template
c5a2: d1 00 ; set drawing flags (C024)
c5a4: 70 b4 ; pen to (y, x)
c5a6: dc ff 0b ; textured flood fill
c5a9: 64 64 ; pen to (y, x)
c5ab: dc ff 11 ; textured flood fill
c5ae: c2 01 ; set room bounding box (preset)
c5b0: c1 34 00 a6 3a 4e ; place object (type, flags, x, y, z)
c5b6: c1 34 00 aa 3a 6e ; place object (type, flags, x, y, z)
c5bc: c1 34 00 a6 3a 8a ; place object (type, flags, x, y, z)
c5c2: c1 34 00 a4 3a 9c ; place object (type, flags, x, y, z)
c5c8: c1 1a 00 28 46 8e ; place object (type, flags, x, y, z)
c5ce: d5 03 6c 5c 30 ; place doorway (type, x, y, z)
c5d3: e7 01 15 6c 5c ae ; room exit
c5d9: d5 00 30 62 5a ; place doorway (type, x, y, z)
c5de: e7 02 0d ac 62 6c ; room exit
c5e4: d5 07 32 6e ae ; place doorway (type, x, y, z)
c5e9: e7 03 06 32 6e 36 ; room exit
c5ef: e9 fe 2e 9e ff 04 ; POKE byte
c5f5: c1 1d 00 2c 38 5a ; place object (type, flags, x, y, z)
c5fb: ee 05 23 ff 96 1f ; evaluate expression
c601: d6 ff 4b ; include template
c604: c1 27 00 64 18 5c ; place object (type, flags, x, y, z)

TEMPLATE 0f
c60a: d6 ff 7b ; include template
c60d: e7 01 07 32 6e 36 ; room exit
c613: e7 02 10 36 6e 32 ; room exit
c619: e7 03 16 32 6e ac ; room exit
c61f: e7 04 4a 64 a0 32 ; room exit
c625: c3 46 00 32 ; set object position
c629: d6 ff 62 ; include template
c62c: c3 1e 00 50 ; set object position
c630: d6 ff 61 ; include template
c633: c3 00 00 00 ; set object position
c637: d6 ff 5e ; include template
c63a: c3 0a 00 0a ; set object position
c63e: d6 ff 60 ; include template

TEMPLATE 10
c641: d6 ff 7a ; include template
c644: e7 01 08 32 6e 36 ; room exit
c64a: e7 02 11 36 6e 32 ; room exit
c650: e9 fe de 9d ff ff ; POKE byte
c656: e7 04 0f ac 6e 32 ; room exit
c65c: c1 17 00 64 4e 32 ; place object (type, flags, x, y, z)
c662: c3 3c 00 32 ; set object position
c666: d6 ff 61 ; include template
c669: c3 14 00 64 ; set object position
c66d: d6 ff 63 ; include template
c670: c3 14 00 14 ; set object position
c674: d6 ff 63 ; include template

TEMPLATE 11
c677: d6 ff 7a ; include template
c67a: e7 01 09 32 6e 36 ; room exit
c680: e7 02 12 36 6e 32 ; room exit
c686: e9 fe de 9d ff ff ; POKE byte
c68c: e7 04 10 ac 6e 32 ; room exit
c692: d6 ff 5e ; include template
c695: c3 10 00 20 ; set object position
c699: d6 ff 5e ; include template
c69c: c3 28 00 28 ; set object position
c6a0: d6 ff 63 ; include template

TEMPLATE 12
c6a3: d6 ff 7a ; include template
c6a6: e7 01 0a 32 6e 36 ; room exit
c6ac: e7 02 13 36 6e 32 ; room exit
c6b2: e9 fe de 9d ff ff ; POKE byte
c6b8: e7 04 11 ac 6e 32 ; room exit
c6be: d5 03 6c 5c 34 ; place doorway (type, x, y, z)
c6c3: e7 05 45 60 5c 92 ; room exit
c6c9: c3 64 00 64 ; set object position
c6cd: d6 ff 63 ; include template
c6d0: c3 32 00 1e ; set object position
c6d4: d6 ff 60 ; include template

TEMPLATE 13
c6d7: d6 ff 7a ; include template
c6da: e7 01 0b 32 6e 36 ; room exit
c6e0: e7 02 14 36 8c 32 ; room exit
c6e6: e7 03 17 32 6e ac ; room exit
c6ec: e7 04 12 ac 6e 32 ; room exit
c6f2: c3 46 00 32 ; set object position
c6f6: d6 ff 62 ; include template
c6f9: c3 0a 00 0a ; set object position
c6fd: d6 ff 60 ; include template
c700: c3 1e 00 50 ; set object position
c704: d6 ff 61 ; include template

TEMPLATE 14
c707: d0 30 ; set attribute
c709: d6 ff 7a ; include template
c70c: e7 01 0c 32 72 36 ; room exit
c712: e7 02 4a 64 a0 32 ; room exit
c718: e7 03 18 32 6e ac ; room exit
c71e: e9 fe e8 9d ff ff ; POKE byte

TEMPLATE 15
c724: d0 28 ; set attribute
c726: 5c 36 ; pen to (y, x)
c728: d7 ff 7f ; include template (save/restore state)
c72b: d1 24 ; set drawing flags (C024)
c72d: da 33 e6 ; move line start
c730: 13 a5 ; pen to (y, x)
c732: 40 00 ; pen to (y, x)
c734: 80 80 ; pen to (y, x)
c736: 34 e6 ; pen to (y, x)
c738: 6f e6 ; pen to (y, x)
c73a: bd 81 ; pen to (y, x)
c73c: 80 81 ; pen to (y, x)
c73e: bd 81 ; pen to (y, x)
c740: 7c 00 ; pen to (y, x)
c742: 7e 00 ; pen to (y, x)
c744: bf 81 ; pen to (y, x)
c746: 6f e8 ; pen to (y, x)
c748: 34 e8 ; pen to (y, x)
c74a: d1 00 ; set drawing flags (C024)
c74c: 65 64 ; pen to (y, x)
c74e: dc ff 11 ; textured flood fill
c751: 6e 47 ; pen to (y, x)
c753: dc 28 ; textured flood fill
c755: 96 96 ; pen to (y, x)
c757: dc ff 0b ; textured flood fill
c75a: 97 78 ; pen to (y, x)
c75c: dc ff 0e ; textured flood fill
c75f: c2 0a ; set room bounding box (preset)
c761: d5 02 66 5c ac ; place doorway (type, x, y, z)
c766: e7 01 0e 6c 5c 34 ; room exit

TEMPLATE 16
c76c: e5 29 ; flag 40: mirror x
c76e: 63 4b ; pen to (y, x)
c770: d6 ff 80 ; include template
c773: d1 00 ; set drawing flags (C024)
c775: d6 ff 7b ; include template
c778: d1 24 ; set drawing flags (C024)
c77a: da 80 80 ; move line start
c77d: bf 80 ; pen to (y, x)
c77f: 80 ff ; pen to (y, x)
c781: d1 00 ; set drawing flags (C024)
c783: b4 81 ; pen to (y, x)
c785: dc ff 0f ; textured flood fill
c788: d5 00 ae 5c 6e ; place doorway (type, x, y, z)
c78d: d5 07 32 6e ae ; place doorway (type, x, y, z)
c792: d5 06 32 6e 32 ; place doorway (type, x, y, z)
c797: e7 01 42 36 5c 5a ; room exit
c79d: e7 02 0f 32 6e 36 ; room exit
c7a3: c3 dc 00 00 ; set object position
c7a7: d6 ff 5d ; include template
c7aa: c3 00 00 00 ; set object position
c7ae: c1 18 00 ac 4a 8c ; place object (type, flags, x, y, z)
c7b4: c1 18 00 ac 4a 4c ; place object (type, flags, x, y, z)
c7ba: c1 18 00 ac 4a 38 ; place object (type, flags, x, y, z)
c7c0: e7 03 4a 6e a0 32 ; room exit
c7c6: c3 74 00 50 ; set object position
c7ca: d6 ff 63 ; include template
c7cd: c3 74 00 32 ; set object position
c7d1: d6 ff 63 ; include template
c7d4: c3 00 00 00 ; set object position
c7d8: c1 0a 00 9a 4a 82 ; place object (type, flags, x, y, z)
c7de: c1 0a 00 9a 4a 64 ; place object (type, flags, x, y, z)

TEMPLATE 17
c7e4: d6 ff 7a ; include template
c7e7: e7 01 13 32 6e 36 ; room exit
c7ed: e7 02 18 36 78 32 ; room exit
c7f3: e7 03 19 32 6e ac ; room exit
c7f9: e9 fe f2 9d ff ff ; POKE byte
c7ff: ee 05 2e ff 5a 1f ; evaluate expression
c805: ee 05 23 ff 05 1f ; evaluate expression
c80b: d6 ff 65 ; include template

TEMPLATE 18
c80e: d0 30 ; set attribute
c810: d6 ff 7a ; include template
c813: e7 01 14 32 6e 36 ; room exit
c819: e7 02 4a 64 a0 32 ; room exit
c81f: e7 03 1a 32 6e ac ; room exit
c825: e9 fe e8 9d ff ff ; POKE byte

TEMPLATE 19
c82b: d6 ff 7a ; include template
c82e: e7 01 17 32 6e 36 ; room exit
c834: e7 02 1a 36 6e 32 ; room exit
c83a: e9 fe de 9d ff ff ; POKE byte
c840: e9 fe f2 9d ff ff ; POKE byte
c846: d5 01 32 5c 6c ; place doorway (type, x, y, z)
c84b: e7 05 3e 92 5c 8a ; room exit
c851: d6 ff 5d ; include template
c854: c3 ec 00 f0 ; set object position
c858: d6 ff 5d ; include template

TEMPLATE 1a
c85b: d0 30 ; set attribute
c85d: d1 24 ; set drawing flags (C024)
c85f: da 00 80 ; move line start
c862: 40 00 ; pen to (y, x)
c864: 80 80 ; pen to (y, x)
c866: 66 93 ; pen to (y, x)
c868: 4d 9a ; pen to (y, x)
c86a: 38 a0 ; pen to (y, x)
c86c: 17 ad ; pen to (y, x)
c86e: 00 80 ; pen to (y, x)
c870: d1 00 ; set drawing flags (C024)
c872: 26 80 ; pen to (y, x)
c874: dc 29 ; textured flood fill
c876: c2 01 ; set room bounding box (preset)
c878: e7 01 18 32 6e 36 ; room exit
c87e: e7 02 4a 64 a0 32 ; room exit
c884: e7 03 29 32 6e ac ; room exit
c88a: e7 04 19 ac 6e 32 ; room exit

TEMPLATE 1b
c890: d6 ff 8b ; include template
c893: d5 01 70 5c 44 ; place doorway (type, x, y, z)
c898: e7 01 1c 34 5c 5a ; room exit
c89e: e7 02 1f 34 5c 5a ; room exit
c8a4: e7 03 20 6c 5c 34 ; room exit
c8aa: e7 04 22 ae 5c 5a ; room exit

TEMPLATE 1c
c8b0: d6 ff 89 ; include template
c8b3: e7 01 1d 74 5c 44 ; room exit
c8b9: d5 01 30 5c 5a ; place doorway (type, x, y, z)
c8be: e7 02 1b ae 5c 44 ; room exit
c8c4: d5 02 6c 5c 30 ; place doorway (type, x, y, z)
c8c9: e7 03 38 88 5c ae ; room exit
c8cf: e9 fe d9 9d ff 80 ; POKE byte
c8d5: e9 fe de 9d ff 02 ; POKE byte

TEMPLATE 1d
c8db: d6 ff 8b ; include template
c8de: e7 01 1f 34 5c 5a ; room exit
c8e4: e7 02 49 60 5c 64 ; room exit
c8ea: e7 03 2a 5a 5c 34 ; room exit
c8f0: d5 01 70 5c 44 ; place doorway (type, x, y, z)
c8f5: e7 04 1c ae 5c 5a ; room exit

TEMPLATE 1e
c8fb: d0 20 ; set attribute
c8fd: 66 27 ; pen to (y, x)
c8ff: d7 ff 87 ; include template (save/restore state)
c902: 63 42 ; pen to (y, x)
c904: d7 ff 80 ; include template (save/restore state)
c907: e5 29 ; flag 40: mirror x
c909: 62 18 ; pen to (y, x)
c90b: d7 ff 80 ; include template (save/restore state)
c90e: 77 42 ; pen to (y, x)
c910: d7 ff 80 ; include template (save/restore state)
c913: e5 28 ; flag 40: mirror x
c915: d7 ff 92 ; include template (save/restore state)
c918: 64 64 ; pen to (y, x)
c91a: dc 29 ; textured flood fill
c91c: d5 00 c4 5c 50 ; place doorway (type, x, y, z)
c921: d5 02 66 5c b2 ; place doorway (type, x, y, z)
c926: e7 01 1c 34 5c 5a ; room exit
c92c: e7 02 2b 5a 5c 34 ; room exit
c932: d5 01 44 5c 50 ; place doorway (type, x, y, z)
c937: e7 03 1f ae 5c 5a ; room exit
c93d: c3 3c 00 28 ; set object position
c941: d6 ff 61 ; include template

TEMPLATE 1f
c944: d6 ff 89 ; include template
c947: e7 01 1e 48 5c 50 ; room exit
c94d: d5 01 30 5c 5a ; place doorway (type, x, y, z)
c952: e7 02 1d ae 5c 44 ; room exit

TEMPLATE 20
c958: d6 ff 89 ; include template
c95b: e7 01 21 74 5c 44 ; room exit
c961: d5 01 30 5c 5a ; place doorway (type, x, y, z)
c966: e7 02 1e c0 5c 50 ; room exit

TEMPLATE 21
c96c: d6 ff 8b ; include template
c96f: d5 01 70 5c 44 ; place doorway (type, x, y, z)
c974: e7 01 22 34 5c 5a ; room exit
c97a: e7 02 35 58 5c 5a ; room exit
c980: e7 03 2c 5a 5c 34 ; room exit
c986: e7 04 20 ae 5c 5a ; room exit

TEMPLATE 22
c98c: 48 24 ; pen to (y, x)
c98e: d7 ff 87 ; include template (save/restore state)
c991: d6 ff 89 ; include template
c994: d5 01 30 5c 5a ; place doorway (type, x, y, z)
c999: e7 01 23 48 5c 82 ; room exit
c99f: e7 02 21 ae 5c 44 ; room exit

TEMPLATE 23
c9a5: d0 20 ; set attribute
c9a7: 67 28 ; pen to (y, x)
c9a9: d7 ff 87 ; include template (save/restore state)
c9ac: 63 42 ; pen to (y, x)
c9ae: d7 ff 80 ; include template (save/restore state)
c9b1: e5 29 ; flag 40: mirror x
c9b3: 65 1e ; pen to (y, x)
c9b5: d7 ff 80 ; include template (save/restore state)
c9b8: 70 2f ; pen to (y, x)
c9ba: d7 ff 7f ; include template (save/restore state)
c9bd: 74 34 ; pen to (y, x)
c9bf: dc ff 0f ; textured flood fill
c9c2: e5 28 ; flag 40: mirror x
c9c4: d6 ff 92 ; include template
c9c7: 64 64 ; pen to (y, x)
c9c9: dc 29 ; textured flood fill
c9cb: d5 00 c4 5c 54 ; place doorway (type, x, y, z)
c9d0: d5 02 66 5c b2 ; place doorway (type, x, y, z)
c9d5: d5 01 44 5c 82 ; place doorway (type, x, y, z)
c9da: e7 01 24 34 5c 5a ; room exit
c9e0: e7 02 2d 5a 5c 34 ; room exit
c9e6: e7 03 22 ae 5c 5a ; room exit
c9ec: c3 28 00 1e ; set object position
c9f0: d6 ff 62 ; include template

TEMPLATE 24
c9f3: d6 ff 89 ; include template
c9f6: e7 01 25 74 5c 58 ; room exit
c9fc: d5 01 30 5c 5a ; place doorway (type, x, y, z)
ca01: e7 02 23 ae 5c 44 ; room exit
ca07: c1 1d 00 64 62 32 ; place object (type, flags, x, y, z)

TEMPLATE 25
ca0d: d6 ff 8a ; include template
ca10: e7 01 26 34 5c 5a ; room exit
ca16: e9 fe ca 9d ff ff ; POKE byte
ca1c: e7 03 20 6c 5c 34 ; room exit
ca22: d5 01 70 5c 58 ; place doorway (type, x, y, z)
ca27: e7 04 24 ae 5c 58 ; room exit

TEMPLATE 26
ca2d: e5 29 ; flag 40: mirror x
ca2f: 4a ac ; pen to (y, x)
ca31: d7 ff 81 ; include template (save/restore state)
ca34: e5 28 ; flag 40: mirror x
ca36: d6 ff 89 ; include template
ca39: d5 01 30 5c 5a ; place doorway (type, x, y, z)
ca3e: e7 01 27 72 5c 60 ; room exit
ca44: e7 02 25 ae 5c 44 ; room exit

TEMPLATE 27
ca4a: d6 ff 8b ; include template
ca4d: d5 01 70 5c 60 ; place doorway (type, x, y, z)
ca52: e7 01 28 34 5c 58 ; room exit
ca58: e7 02 36 56 5c 62 ; room exit
ca5e: e7 03 3a 6c 5c 34 ; room exit
ca64: e7 04 26 ae 5c 58 ; room exit

TEMPLATE 28
ca6a: 48 1f ; pen to (y, x)
ca6c: d7 ff 87 ; include template (save/restore state)
ca6f: 3d 08 ; pen to (y, x)
ca71: d7 ff 87 ; include template (save/restore state)
ca74: d6 ff 89 ; include template
ca77: d5 01 30 5c 58 ; place doorway (type, x, y, z)
ca7c: e7 01 3d 5e 5c 6c ; room exit
ca82: e7 02 27 ae 5c 44 ; room exit
ca88: c1 1d 00 64 62 4a ; place object (type, flags, x, y, z)

TEMPLATE 29
ca8e: d0 30 ; set attribute
ca90: d1 24 ; set drawing flags (C024)
ca92: da 40 00 ; move line start
ca95: 57 2d ; pen to (y, x)
ca97: 4c 6d ; pen to (y, x)
ca99: 44 88 ; pen to (y, x)
ca9b: 61 b8 ; pen to (y, x)
ca9d: 3f ff ; pen to (y, x)
ca9f: 00 80 ; pen to (y, x)
caa1: 40 00 ; pen to (y, x)
caa3: d1 00 ; set drawing flags (C024)
caa5: 32 80 ; pen to (y, x)
caa7: dc 29 ; textured flood fill
caa9: c2 01 ; set room bounding box (preset)
caab: d5 01 30 5c 6c ; place doorway (type, x, y, z)
cab0: e7 01 44 9c 5c 8a ; room exit
cab6: d6 ff 5b ; include template
cab9: e7 02 1a 32 6e 36 ; room exit
cabf: e7 03 4a 64 a0 32 ; room exit
cac5: e7 04 30 32 6e aa ; room exit
cacb: d5 04 6e 6e 6e ; place doorway (type, x, y, z)
cad0: d5 07 6e 6e 6e ; place doorway (type, x, y, z)
cad5: e7 05 4a 64 a0 32 ; room exit
cadb: e7 06 4a 32 a0 32 ; room exit

TEMPLATE 2a
cae1: d6 fe 5f 00 ; include template
cae5: 64 71 ; pen to (y, x)
cae7: dc ff 0e ; textured flood fill
caea: 46 64 ; pen to (y, x)
caec: dc 29 ; textured flood fill
caee: d5 03 5a 5c 30 ; place doorway (type, x, y, z)
caf3: e7 01 1f 34 5c 5a ; room exit
caf9: e7 02 31 78 5c 34 ; room exit
caff: e7 03 1d 88 5c ae ; room exit
cb05: e9 fe ca 9d 29 ; POKE byte

TEMPLATE 2b
cb0a: d6 ff 5f ; include template
cb0d: 64 71 ; pen to (y, x)
cb0f: dc ff 0b ; textured flood fill
cb12: 46 64 ; pen to (y, x)
cb14: dc 2c ; textured flood fill
cb16: d5 03 5a 5c 30 ; place doorway (type, x, y, z)
cb1b: e7 01 20 34 5c 5a ; room exit
cb21: e7 02 32 76 5c 36 ; room exit
cb27: e7 03 1e 66 5c b0 ; room exit
cb2d: e9 fe ca 9d ff 05 ; POKE byte

TEMPLATE 2c
cb33: d6 fe 5f 00 ; include template
cb37: 73 78 ; pen to (y, x)
cb39: dc ff 06 ; textured flood fill
cb3c: 46 64 ; pen to (y, x)
cb3e: dc ff 0d ; textured flood fill
cb41: e9 fe b6 9d ff ff ; POKE byte
cb47: e7 02 20 5a 5c 34 ; room exit
cb4d: d5 03 5a 5c 30 ; place doorway (type, x, y, z)
cb52: e7 03 21 88 5c ac ; room exit

TEMPLATE 2d
cb58: d6 fe 5f 00 ; include template
cb5c: 64 71 ; pen to (y, x)
cb5e: dc ff 0e ; textured flood fill
cb61: 46 64 ; pen to (y, x)
cb63: dc 29 ; textured flood fill
cb65: c1 18 00 7a 4a 8c ; place object (type, flags, x, y, z)
cb6b: c1 18 00 7a 4a 4c ; place object (type, flags, x, y, z)
cb71: c1 18 00 7a 4a 38 ; place object (type, flags, x, y, z)
cb77: d5 03 5a 5c 30 ; place doorway (type, x, y, z)
cb7c: e7 01 33 74 5c 5a ; room exit
cb82: e7 02 26 6c 5c 34 ; room exit
cb88: e7 03 23 66 5c b0 ; room exit

TEMPLATE 2e
cb8e: 44 4a ; pen to (y, x)
cb90: d7 ff 80 ; include template (save/restore state)
cb93: 59 6f ; pen to (y, x)
cb95: d7 ff 7f ; include template (save/restore state)
cb98: 87 c4 ; pen to (y, x)
cb9a: d7 ff 81 ; include template (save/restore state)
cb9d: d6 ff 89 ; include template
cba0: 60 77 ; pen to (y, x)
cba2: dc ff 0e ; textured flood fill
cba5: d5 02 4e 5c 90 ; place doorway (type, x, y, z)
cbaa: d5 02 84 5c 90 ; place doorway (type, x, y, z)
cbaf: e7 01 44 86 5c 8c ; room exit
cbb5: e7 02 3e 6c 5c 5e ; room exit
cbbb: e7 03 37 6c 5c 36 ; room exit

TEMPLATE 2f
cbc1: d5 01 30 70 64 ; place doorway (type, x, y, z)
cbc6: c5 ; clear window
cbc7: e7 01 48 aa 5c 8c ; room exit
cbcd: d0 10 ; set attribute
cbcf: d1 24 ; set drawing flags (C024)
cbd1: da 40 ff ; move line start
cbd4: 2a c6 ; pen to (y, x)
cbd6: 00 80 ; pen to (y, x)
cbd8: 30 27 ; pen to (y, x)
cbda: 40 00 ; pen to (y, x)
cbdc: 57 2e ; pen to (y, x)
cbde: 55 4a ; pen to (y, x)
cbe0: 50 5b ; pen to (y, x)
cbe2: 5d 90 ; pen to (y, x)
cbe4: 56 d3 ; pen to (y, x)
cbe6: 40 ff ; pen to (y, x)
cbe8: da 58 30 ; move line start
cbeb: 75 32 ; pen to (y, x)
cbed: 6f 59 ; pen to (y, x)
cbef: 77 90 ; pen to (y, x)
cbf1: 71 cd ; pen to (y, x)
cbf3: 56 d1 ; pen to (y, x)
cbf5: da 75 32 ; move line start
cbf8: 9a 7c ; pen to (y, x)
cbfa: 8e 9c ; pen to (y, x)
cbfc: 72 cb ; pen to (y, x)
cbfe: da 6b 58 ; move line start
cc01: 56 54 ; pen to (y, x)
cc03: da 5f 87 ; move line start
cc06: 70 85 ; pen to (y, x)
cc08: da 68 aa ; move line start
cc0b: 5d ad ; pen to (y, x)
cc0d: 70 ab ; pen to (y, x)
cc0f: e4 28 ; flag 20: pen down
cc11: 6f 55 ; pen to (y, x)
cc13: dc 28 ; textured flood fill
cc15: 73 ad ; pen to (y, x)
cc17: dc 28 ; textured flood fill
cc19: 4d 62 ; pen to (y, x)
cc1b: dc 29 ; textured flood fill
cc1d: 8c 64 ; pen to (y, x)
cc1f: dc 29 ; textured flood fill
cc21: 01 48 ; pen to (y, x)
cc23: e2 28 ; flag 04: chain lines
cc25: c2 01 ; set room bounding box (preset)
cc27: c1 1b 00 68 52 96 ; place object (type, flags, x, y, z)
cc2d: c1 1b 00 66 42 94 ; place object (type, flags, x, y, z)
cc33: c1 20 00 9a 52 7a ; place object (type, flags, x, y, z)

TEMPLATE 30
cc39: d0 30 ; set attribute
cc3b: d1 24 ; set drawing flags (C024)
cc3d: da 40 00 ; move line start
cc40: 80 80 ; pen to (y, x)
cc42: 5a 98 ; pen to (y, x)
cc44: 40 c5 ; pen to (y, x)
cc46: 31 a6 ; pen to (y, x)
cc48: 1f 43 ; pen to (y, x)
cc4a: 40 00 ; pen to (y, x)
cc4c: e4 28 ; flag 20: pen down
cc4e: e2 28 ; flag 04: chain lines
cc50: 28 64 ; pen to (y, x)
cc52: dc 29 ; textured flood fill
cc54: c2 01 ; set room bounding box (preset)
cc56: ee 05 20 ff 29 1f ; evaluate expression
cc5c: d6 ff 5b ; include template
cc5f: e7 01 29 32 6e 36 ; room exit
cc65: e7 02 4a 64 a0 32 ; room exit
cc6b: d5 05 32 6e 50 ; place doorway (type, x, y, z)
cc70: e7 04 4a 32 98 64 ; room exit
cc76: d5 03 74 5c 54 ; place doorway (type, x, y, z)
cc7b: e7 05 34 54 72 ae ; room exit

TEMPLATE 31
cc81: d0 10 ; set attribute
cc83: 55 7d ; pen to (y, x)
cc85: d7 ff 7e ; include template (save/restore state)
cc88: d7 ff 8d ; include template (save/restore state)
cc8b: d5 03 78 5c 30 ; place doorway (type, x, y, z)
cc90: e7 01 2a 5c 5c b8 ; room exit
cc96: d5 08 82 34 78 ; place doorway (type, x, y, z)
cc9b: e7 02 48 64 64 78 ; room exit

TEMPLATE 32
cca1: 6e 29 ; pen to (y, x)
cca3: d7 ff 87 ; include template (save/restore state)
cca6: d6 ff 8d ; include template
cca9: d5 03 76 5c 30 ; place doorway (type, x, y, z)
ccae: e7 01 2b 5c 5c b8 ; room exit

TEMPLATE 33
ccb4: 72 67 ; pen to (y, x)
ccb6: d7 ff 80 ; include template (save/restore state)
ccb9: d7 ff 8d ; include template (save/restore state)
ccbc: d5 02 8a 5c b0 ; place doorway (type, x, y, z)
ccc1: d5 01 70 5c 5a ; place doorway (type, x, y, z)
ccc6: e7 01 3c a2 5c 4e ; room exit
cccc: e7 02 2d 78 5c 7c ; room exit

TEMPLATE 34
ccd2: fa ff 00 ff ab ; set origin (x, y)
ccd7: c1 1d 00 5a 48 22 ; place object (type, flags, x, y, z)
ccdd: c1 1d 00 5a 48 36 ; place object (type, flags, x, y, z)
cce3: c1 1d 00 5a 48 4a ; place object (type, flags, x, y, z)
cce9: c1 1d 00 5a 48 5e ; place object (type, flags, x, y, z)
ccef: c1 1d 00 5a 48 72 ; place object (type, flags, x, y, z)
ccf5: c1 1d 00 5a 48 86 ; place object (type, flags, x, y, z)
ccfb: c1 1d 00 5a 48 9a ; place object (type, flags, x, y, z)
cd01: c5 ; clear window
cd02: d0 28 ; set attribute
cd04: d1 24 ; set drawing flags (C024)
cd06: da 8b 37 ; move line start
cd09: 41 cb ; pen to (y, x)
cd0b: 33 b0 ; pen to (y, x)
cd0d: 7d 1b ; pen to (y, x)
cd0f: 8a 36 ; pen to (y, x)
cd11: 7d 1b ; pen to (y, x)
cd13: 6e 20 ; pen to (y, x)
cd15: 58 31 ; pen to (y, x)
cd17: 53 51 ; pen to (y, x)
cd19: 4b 6a ; pen to (y, x)
cd1b: 33 8b ; pen to (y, x)
cd1d: 1a c0 ; pen to (y, x)
cd1f: da 32 b0 ; move line start
cd22: 26 b4 ; pen to (y, x)
cd24: 1b bf ; pen to (y, x)
cd26: 1c c5 ; pen to (y, x)
cd28: 2e cb ; pen to (y, x)
cd2a: 40 cb ; pen to (y, x)
cd2c: d1 00 ; set drawing flags (C024)
cd2e: 60 51 ; pen to (y, x)
cd30: dc 28 ; textured flood fill
cd32: 34 b0 ; pen to (y, x)
cd34: dc 29 ; textured flood fill
cd36: 3d c8 ; pen to (y, x)
cd38: dc 2b ; textured flood fill
cd3a: c2 0c ; set room bounding box (preset)
cd3c: c1 20 00 54 48 22 ; place object (type, flags, x, y, z)
cd42: d5 07 32 84 b6 ; place doorway (type, x, y, z)
cd47: e7 01 30 50 6e 56 ; room exit
cd4d: d5 05 32 84 28 ; place doorway (type, x, y, z)
cd52: e7 02 39 32 6e aa ; room exit
cd58: e9 fe 24 9d ff 07 ; POKE byte
cd5e: fa ff 00 ff 00 ; set origin (x, y)

TEMPLATE 35
cd63: d6 ff 8e ; include template
cd66: d5 01 54 5c 5a ; place doorway (type, x, y, z)
cd6b: e7 01 21 ae 5c 88 ; room exit
cd71: c1 1d 00 9e 46 46 ; place object (type, flags, x, y, z)
cd77: c1 1d 00 9e 46 32 ; place object (type, flags, x, y, z)

TEMPLATE 36
cd7d: 5b 4a ; pen to (y, x)
cd7f: d7 ff 87 ; include template (save/restore state)
cd82: d6 ff 8e ; include template
cd85: d5 01 54 5c 62 ; place doorway (type, x, y, z)
cd8a: e7 01 27 ae 5c 88 ; room exit
cd90: c1 1d 00 9e 46 7e ; place object (type, flags, x, y, z)
cd96: c1 1d 00 9e 46 6a ; place object (type, flags, x, y, z)

TEMPLATE 37
cd9c: d6 ff 8e ; include template
cd9f: d5 03 6c 5c 32 ; place doorway (type, x, y, z)
cda4: e7 01 2e 84 5c 90 ; room exit
cdaa: c1 01 00 64 3c 64 ; place object (type, flags, x, y, z)
cdb0: c1 01 00 64 46 64 ; place object (type, flags, x, y, z)
cdb6: c1 01 00 64 50 64 ; place object (type, flags, x, y, z)
cdbc: c1 05 00 64 5a 60 ; place object (type, flags, x, y, z)

TEMPLATE 38
cdc2: e5 29 ; flag 40: mirror x
cdc4: 58 32 ; pen to (y, x)
cdc6: d7 ff 80 ; include template (save/restore state)
cdc9: e5 28 ; flag 40: mirror x
cdcb: 6e 5a ; pen to (y, x)
cdcd: d7 ff 7f ; include template (save/restore state)
cdd0: d6 ff 8d ; include template
cdd3: 77 62 ; pen to (y, x)
cdd5: dc ff 0e ; textured flood fill
cdd8: d5 02 8e 5c b0 ; place doorway (type, x, y, z)
cddd: d5 00 ae 5c 54 ; place doorway (type, x, y, z)
cde2: e7 01 1c 6c 5c 34 ; room exit
cde8: e7 02 47 8c 5c 8c ; room exit
cdee: d5 01 70 5c 7c ; place doorway (type, x, y, z)
cdf3: e7 03 22 ae 5c 5a ; room exit
cdf9: e9 fe ca 9d ff 03 ; POKE byte

TEMPLATE 39
cdff: d0 30 ; set attribute
ce01: d1 24 ; set drawing flags (C024)
ce03: da 40 ff ; move line start
ce06: 00 80 ; pen to (y, x)
ce08: 29 2e ; pen to (y, x)
ce0a: 38 1c ; pen to (y, x)
ce0c: 4b 15 ; pen to (y, x)
ce0e: 58 2f ; pen to (y, x)
ce10: 4d 6b ; pen to (y, x)
ce12: 52 9d ; pen to (y, x)
ce14: 41 ff ; pen to (y, x)
ce16: d1 00 ; set drawing flags (C024)
ce18: 3c 64 ; pen to (y, x)
ce1a: dc 29 ; textured flood fill
ce1c: c2 01 ; set room bounding box (preset)
ce1e: ee 05 20 ff 29 1f ; evaluate expression
ce24: d6 ff 5b ; include template
ce27: e7 01 34 3c 84 32 ; room exit
ce2d: e7 02 4a 64 a0 32 ; room exit
ce33: e7 03 3b 32 6e ae ; room exit
ce39: d5 01 30 5c 64 ; place doorway (type, x, y, z)
ce3e: e7 04 3d c6 5c 5e ; room exit

TEMPLATE 3a
ce44: e5 29 ; flag 40: mirror x
ce46: 61 15 ; pen to (y, x)
ce48: d7 ff 87 ; include template (save/restore state)
ce4b: e5 28 ; flag 40: mirror x
ce4d: 61 55 ; pen to (y, x)
ce4f: d7 ff 87 ; include template (save/restore state)
ce52: 52 37 ; pen to (y, x)
ce54: d7 ff 87 ; include template (save/restore state)
ce57: 3d 0d ; pen to (y, x)
ce59: d7 ff 87 ; include template (save/restore state)
ce5c: d6 ff 89 ; include template
ce5f: e7 01 3c 5c 5c 6c ; room exit
ce65: d5 03 6c 5c 30 ; place doorway (type, x, y, z)
ce6a: e7 02 27 88 5c ae ; room exit

TEMPLATE 3b
ce70: d0 20 ; set attribute
ce72: d1 24 ; set drawing flags (C024)
ce74: da 40 00 ; move line start
ce77: 80 80 ; pen to (y, x)
ce79: 67 ad ; pen to (y, x)
ce7b: 75 da ; pen to (y, x)
ce7d: 51 d3 ; pen to (y, x)
ce7f: 40 ff ; pen to (y, x)
ce81: 2e c1 ; pen to (y, x)
ce83: 19 9f ; pen to (y, x)
ce85: 10 70 ; pen to (y, x)
ce87: 07 5c ; pen to (y, x)
ce89: 3f 00 ; pen to (y, x)
ce8b: da 80 80 ; move line start
ce8e: a7 8b ; pen to (y, x)
ce90: bf 95 ; pen to (y, x)
ce92: da 68 ae ; move line start
ce95: 88 b7 ; pen to (y, x)
ce97: 93 bf ; pen to (y, x)
ce99: 95 c9 ; pen to (y, x)
ce9b: 8e d4 ; pen to (y, x)
ce9d: 87 d9 ; pen to (y, x)
ce9f: 75 da ; pen to (y, x)
cea1: da 95 b2 ; move line start
cea4: 8c a6 ; pen to (y, x)
cea6: da 9e ad ; move line start
cea9: 81 a4 ; pen to (y, x)
ceab: d1 00 ; set drawing flags (C024)
cead: a0 ff ; pen to (y, x)
ceaf: dc 28 ; textured flood fill
ceb1: 6e b2 ; pen to (y, x)
ceb3: dc 2b ; textured flood fill
ceb5: 64 80 ; pen to (y, x)
ceb7: dc 29 ; textured flood fill
ceb9: c2 01 ; set room bounding box (preset)
cebb: d5 07 32 6e ae ; place doorway (type, x, y, z)
cec0: e7 01 39 32 6e 36 ; room exit
cec6: d5 00 ae 5c 64 ; place doorway (type, x, y, z)
cecb: e7 02 41 46 5c 90 ; room exit
ced1: c3 1e 00 46 ; set object position
ced5: d6 ff 60 ; include template
ced8: c3 3c 00 28 ; set object position
cedc: d6 ff 61 ; include template

TEMPLATE 3c
cedf: 58 67 ; pen to (y, x)
cee1: d7 ff 80 ; include template (save/restore state)
cee4: 64 64 ; pen to (y, x)
cee6: d7 ff 90 ; include template (save/restore state)
cee9: 64 96 ; pen to (y, x)
ceeb: dc ff 0d ; textured flood fill
ceee: aa 96 ; pen to (y, x)
cef0: dc ff 10 ; textured flood fill
cef3: aa be ; pen to (y, x)
cef5: dc ff 0f ; textured flood fill
cef8: d5 02 6e 5c 94 ; place doorway (type, x, y, z)
cefd: e7 01 44 88 5c 8c ; room exit
cf03: d5 01 5a 5c 6c ; place doorway (type, x, y, z)
cf08: e7 02 3a ae 5c 58 ; room exit
cf0e: d5 03 a2 5c 4a ; place doorway (type, x, y, z)
cf13: e7 03 33 88 5c ae ; room exit
cf19: c1 1c 00 5c aa 2a ; place object (type, flags, x, y, z)

TEMPLATE 3d
cf1f: e5 29 ; flag 40: mirror x
cf21: 6a 25 ; pen to (y, x)
cf23: d7 ff 80 ; include template (save/restore state)
cf26: e5 28 ; flag 40: mirror x
cf28: 64 64 ; pen to (y, x)
cf2a: d7 ff 90 ; include template (save/restore state)
cf2d: 64 96 ; pen to (y, x)
cf2f: dc ff 01 ; textured flood fill
cf32: aa 96 ; pen to (y, x)
cf34: dc ff 0e ; textured flood fill
cf37: aa be ; pen to (y, x)
cf39: dc ff 0e ; textured flood fill
cf3c: d5 00 c6 5c 5e ; place doorway (type, x, y, z)
cf41: d5 01 5a 5c 6c ; place doorway (type, x, y, z)
cf46: e7 01 39 34 5c 6c ; room exit
cf4c: e7 02 28 ae 5c 58 ; room exit
cf52: c1 1c 00 5c aa 2a ; place object (type, flags, x, y, z)

TEMPLATE 3e
cf58: e5 29 ; flag 40: mirror x
cf5a: 64 64 ; pen to (y, x)
cf5c: d7 ff 90 ; include template (save/restore state)
cf5f: 65 81 ; pen to (y, x)
cf61: d7 ff 80 ; include template (save/restore state)
cf64: e5 28 ; flag 40: mirror x
cf66: 96 46 ; pen to (y, x)
cf68: dc ff 10 ; textured flood fill
cf6b: 96 50 ; pen to (y, x)
cf6d: dc ff 06 ; textured flood fill
cf70: 64 64 ; pen to (y, x)
cf72: dc ff 0d ; textured flood fill
cf75: c2 0b ; set room bounding box (preset)
cf77: d5 00 94 5c 8a ; place doorway (type, x, y, z)
cf7c: d5 03 6c 5c 5a ; place doorway (type, x, y, z)
cf81: e7 01 19 36 5c 6c ; room exit
cf87: e7 02 2e 4e 5c 8e ; room exit
cf8d: c1 1c 00 2a aa 5c ; place object (type, flags, x, y, z)

TEMPLATE 3f
cf93: d7 ff 90 ; include template (save/restore state)
cf96: aa 96 ; pen to (y, x)
cf98: dc ff 0e ; textured flood fill
cf9b: aa be ; pen to (y, x)
cf9d: dc ff 0f ; textured flood fill
cfa0: 64 c8 ; pen to (y, x)
cfa2: dc ff 04 ; textured flood fill
cfa5: d5 01 5a 5c 6c ; place doorway (type, x, y, z)
cfaa: e7 01 42 ac 5c 5a ; room exit
cfb0: d5 03 a2 5c 4a ; place doorway (type, x, y, z)
cfb5: e7 02 40 6c 5c aa ; room exit
cfbb: c1 1c 00 5c aa 2a ; place object (type, flags, x, y, z)

TEMPLATE 40
cfc1: d0 10 ; set attribute
cfc3: 32 80 ; pen to (y, x)
cfc5: d7 ff 7e ; include template (save/restore state)
cfc8: 63 49 ; pen to (y, x)
cfca: d7 ff 80 ; include template (save/restore state)
cfcd: d7 ff 7a ; include template (save/restore state)
cfd0: d5 02 6c 5c ac ; place doorway (type, x, y, z)
cfd5: e7 01 3f a2 5c 4e ; room exit
cfdb: d5 08 64 34 50 ; place doorway (type, x, y, z)
cfe0: e7 02 2f 64 78 64 ; room exit

TEMPLATE 41
cfe6: d0 10 ; set attribute
cfe8: d1 24 ; set drawing flags (C024)
cfea: da 4c 0d ; move line start
cfed: 32 41 ; pen to (y, x)
cfef: 49 6f ; pen to (y, x)
cff1: 4f 87 ; pen to (y, x)
cff3: 4e 98 ; pen to (y, x)
cff5: 46 af ; pen to (y, x)
cff7: 60 e4 ; pen to (y, x)
cff9: 73 ab ; pen to (y, x)
cffb: 7c 82 ; pen to (y, x)
cffd: 78 6b ; pen to (y, x)
cfff: 62 39 ; pen to (y, x)
d001: 4c 0d ; pen to (y, x)
d003: d1 00 ; set drawing flags (C024)
d005: 64 80 ; pen to (y, x)
d007: dc 29 ; textured flood fill
d009: c2 0f ; set room bounding box (preset)
d00b: d5 01 42 5c 90 ; place doorway (type, x, y, z)
d010: e7 01 3b aa 5c 64 ; room exit
d016: d5 03 98 5c 5e ; place doorway (type, x, y, z)
d01b: e7 02 46 74 70 a8 ; room exit

TEMPLATE 42
d021: d6 ff 89 ; include template
d024: d5 01 30 5c 56 ; place doorway (type, x, y, z)
d029: e7 01 3f 5e 5c 6c ; room exit
d02f: e7 02 16 ac 5c 6e ; room exit

TEMPLATE 43
d035: 54 65 ; pen to (y, x)
d037: d7 ff 7f ; include template (save/restore state)
d03a: 42 41 ; pen to (y, x)
d03c: d7 ff 7f ; include template (save/restore state)
d03f: d6 ff 89 ; include template
d042: 5a 6a ; pen to (y, x)
d044: dc ff 07 ; textured flood fill
d047: 46 46 ; pen to (y, x)
d049: dc ff 07 ; textured flood fill
d04c: d5 01 34 5c 58 ; place doorway (type, x, y, z)
d051: d5 03 6c 5c 30 ; place doorway (type, x, y, z)
d056: e7 01 45 5c 5c 6a ; room exit
d05c: e7 02 2e ac 5c 58 ; room exit
d062: e7 03 2e 4e 5c 8e ; room exit

TEMPLATE 44
d068: 79 38 ; pen to (y, x)
d06a: d7 ff 87 ; include template (save/restore state)
d06d: e5 29 ; flag 40: mirror x
d06f: 6b 7a ; pen to (y, x)
d071: d7 ff 80 ; include template (save/restore state)
d074: e5 28 ; flag 40: mirror x
d076: d6 ff 8f ; include template
d079: d5 00 9e 5c 8a ; place doorway (type, x, y, z)
d07e: d5 01 84 5c 8c ; place doorway (type, x, y, z)
d083: d5 03 88 5c 88 ; place doorway (type, x, y, z)
d088: e7 01 29 32 5c 6c ; room exit
d08e: e7 02 2e ac 5c 58 ; room exit
d094: e7 03 3c 6e 5c 92 ; room exit
d09a: e9 fe de 9d ff 04 ; POKE byte

TEMPLATE 45
d0a0: 4b 48 ; pen to (y, x)
d0a2: d7 ff 7f ; include template (save/restore state)
d0a5: 64 64 ; pen to (y, x)
d0a7: d7 ff 90 ; include template (save/restore state)
d0aa: aa 96 ; pen to (y, x)
d0ac: dc ff 10 ; textured flood fill
d0af: aa be ; pen to (y, x)
d0b1: dc ff 0f ; textured flood fill
d0b4: 67 96 ; pen to (y, x)
d0b6: dc 2c ; textured flood fill
d0b8: 4f 4d ; pen to (y, x)
d0ba: dc ff 0b ; textured flood fill
d0bd: d5 02 60 5c 94 ; place doorway (type, x, y, z)
d0c2: e7 01 12 6c 5c 36 ; room exit
d0c8: d5 01 5a 5c 6a ; place doorway (type, x, y, z)
d0cd: e7 02 43 ac 5c 58 ; room exit
d0d3: c1 1c 00 5c aa 2a ; place object (type, flags, x, y, z)

TEMPLATE 46
d0d9: d0 10 ; set attribute
d0db: d1 24 ; set drawing flags (C024)
d0dd: da 30 e1 ; move line start
d0e0: 0e a6 ; pen to (y, x)
d0e2: 00 80 ; pen to (y, x)
d0e4: 1a 41 ; pen to (y, x)
d0e6: 40 00 ; pen to (y, x)
d0e8: 58 31 ; pen to (y, x)
d0ea: 53 51 ; pen to (y, x)
d0ec: 57 6f ; pen to (y, x)
d0ee: 4c 8d ; pen to (y, x)
d0f0: 41 bd ; pen to (y, x)
d0f2: 30 e0 ; pen to (y, x)
d0f4: 45 e2 ; pen to (y, x)
d0f6: 55 c2 ; pen to (y, x)
d0f8: 60 8f ; pen to (y, x)
d0fa: 69 72 ; pen to (y, x)
d0fc: 66 50 ; pen to (y, x)
d0fe: 6a 35 ; pen to (y, x)
d100: 59 33 ; pen to (y, x)
d102: da 45 e2 ; move line start
d105: 53 ff ; pen to (y, x)
d107: 91 82 ; pen to (y, x)
d109: 7e 54 ; pen to (y, x)
d10b: 6b 37 ; pen to (y, x)
d10d: d1 00 ; set drawing flags (C024)
d10f: 6c 68 ; pen to (y, x)
d111: dc 29 ; textured flood fill
d113: 64 64 ; pen to (y, x)
d115: dc 28 ; textured flood fill
d117: 3c 64 ; pen to (y, x)
d119: dc 29 ; textured flood fill
d11b: c2 01 ; set room bounding box (preset)
d11d: d5 03 74 70 ac ; place doorway (type, x, y, z)
d122: e7 01 41 98 5c 62 ; room exit
d128: e9 fe b1 9d ff 40 ; POKE byte
d12e: c1 1b 00 86 46 6a ; place object (type, flags, x, y, z)
d134: c1 1b 00 68 46 96 ; place object (type, flags, x, y, z)
d13a: c1 20 00 94 46 32 ; place object (type, flags, x, y, z)

TEMPLATE 47
d140: e5 29 ; flag 40: mirror x
d142: 78 3d ; pen to (y, x)
d144: d7 ff 87 ; include template (save/restore state)
d147: e5 28 ; flag 40: mirror x
d149: d6 ff 8f ; include template
d14c: d5 01 86 5c 8c ; place doorway (type, x, y, z)
d151: e7 01 38 ac 5c 54 ; room exit

TEMPLATE 48
d157: d0 10 ; set attribute
d159: d1 24 ; set drawing flags (C024)
d15b: da 74 9b ; move line start
d15e: 5b ce ; pen to (y, x)
d160: 44 a7 ; pen to (y, x)
d162: 36 81 ; pen to (y, x)
d164: 23 62 ; pen to (y, x)
d166: 35 44 ; pen to (y, x)
d168: 47 1b ; pen to (y, x)
d16a: 63 49 ; pen to (y, x)
d16c: 7a 84 ; pen to (y, x)
d16e: 79 9a ; pen to (y, x)
d170: 75 9a ; pen to (y, x)
d172: 91 98 ; pen to (y, x)
d174: 9c 94 ; pen to (y, x)
d176: 9e 88 ; pen to (y, x)
d178: 7b 83 ; pen to (y, x)
d17a: da 48 1c ; move line start
d17d: 7d 23 ; pen to (y, x)
d17f: a2 2e ; pen to (y, x)
d181: a4 32 ; pen to (y, x)
d183: a2 3f ; pen to (y, x)
d185: a6 45 ; pen to (y, x)
d187: ad 63 ; pen to (y, x)
d189: b7 7c ; pen to (y, x)
d18b: b9 88 ; pen to (y, x)
d18d: b1 a5 ; pen to (y, x)
d18f: 9e c3 ; pen to (y, x)
d191: 8e ce ; pen to (y, x)
d193: 5b ce ; pen to (y, x)
d195: da 9e 88 ; move line start
d198: a3 80 ; pen to (y, x)
d19a: da 6b 4e ; move line start
d19d: 92 57 ; pen to (y, x)
d19f: da 7c 9b ; move line start
d1a2: 96 a0 ; pen to (y, x)
d1a4: d1 00 ; set drawing flags (C024)
d1a6: 64 64 ; pen to (y, x)
d1a8: dc 29 ; textured flood fill
d1aa: 8c 96 ; pen to (y, x)
d1ac: dc 2b ; textured flood fill
d1ae: aa 96 ; pen to (y, x)
d1b0: dc ff 09 ; textured flood fill
d1b3: c2 0d ; set room bounding box (preset)
d1b5: d5 00 ae 5c 94 ; place doorway (type, x, y, z)
d1ba: e7 01 2f 34 78 64 ; room exit
d1c0: d5 03 8c 70 62 ; place doorway (type, x, y, z)
d1c5: e7 02 49 60 5c 9a ; room exit

TEMPLATE 49
d1cb: d0 10 ; set attribute
d1cd: d1 24 ; set drawing flags (C024)
d1cf: da 8e a8 ; move line start
d1d2: 68 6e ; pen to (y, x)
d1d4: 4a 43 ; pen to (y, x)
d1d6: 3d 63 ; pen to (y, x)
d1d8: 2f 80 ; pen to (y, x)
d1da: 25 9a ; pen to (y, x)
d1dc: 51 ce ; pen to (y, x)
d1de: 64 ed ; pen to (y, x)
d1e0: 77 c7 ; pen to (y, x)
d1e2: 8e a7 ; pen to (y, x)
d1e4: bf a7 ; pen to (y, x)
d1e6: da 5a 5a ; move line start
d1e9: 99 5a ; pen to (y, x)
d1eb: bf a6 ; pen to (y, x)
d1ed: 9b ed ; pen to (y, x)
d1ef: 65 ed ; pen to (y, x)
d1f1: da 5a 5b ; move line start
d1f4: 5d 56 ; pen to (y, x)
d1f6: 9a 56 ; pen to (y, x)
d1f8: bf a1 ; pen to (y, x)
d1fa: da bf ac ; move line start
d1fd: 9d f1 ; pen to (y, x)
d1ff: 67 f1 ; pen to (y, x)
d201: 63 ed ; pen to (y, x)
d203: d1 00 ; set drawing flags (C024)
d205: 64 64 ; pen to (y, x)
d207: dc ff 10 ; textured flood fill
d20a: 90 aa ; pen to (y, x)
d20c: dc ff 0f ; textured flood fill
d20f: 36 96 ; pen to (y, x)
d211: dc 29 ; textured flood fill
d213: c2 0e ; set room bounding box (preset)
d215: d5 02 60 5c 9e ; place doorway (type, x, y, z)
d21a: d5 01 5c 5c 64 ; place doorway (type, x, y, z)
d21f: e7 01 48 8c 78 68 ; room exit
d225: e7 02 1d ae 5c 88 ; room exit

TEMPLATE 4a
d22b: d0 28 ; set attribute
d22d: e4 29 ; flag 20: pen down
d22f: da 64 64 ; move line start
d232: b7 5f ; pen to (y, x)
d234: da 3a 94 ; move line start
d237: 9e 85 ; pen to (y, x)
d239: da 55 c2 ; move line start
d23c: af ba ; pen to (y, x)
d23e: e2 29 ; flag 04: chain lines
d240: da 32 ff ; move line start
d243: 3d c3 ; pen to (y, x)
d245: 38 94 ; pen to (y, x)
d247: 52 44 ; pen to (y, x)
d249: 58 00 ; pen to (y, x)
d24b: d1 00 ; set drawing flags (C024)
d24d: bf 00 ; pen to (y, x)
d24f: dc 28 ; textured flood fill
d251: c2 01 ; set room bounding box (preset)
d253: e9 fe 24 9d ff 07 ; POKE byte

TEMPLATE 4b
d259: e9 fe 56 c0 23 ; POKE byte
d25e: c1 28 00 64 0a 64 ; place object (type, flags, x, y, z)
d264: ee 07 23 23 02 ff 10 1f ; evaluate expression
d26c: ef 23 11 ff 32 01 ; conditional skip
d272: fd ; loop back to start of template

TEMPLATE 4c
d273: ee 0d 24 09 ff fe 28 05 ff 1f 07 ff 1f 1f ; evaluate expression
d281: ef 24 0d 28 01 ; conditional skip
d286: fd ; loop back to start of template
d287: ec 0f 30 20 54 4f 20 45 4e 44 20 47 41 4d 45 1f ; print text "0 TO END GAME"

TEMPLATE 4d
d297: cf 22 ; increment variable
d299: dd 22 ; set border colour
d29b: dd 22 ; set border colour
d29d: cf 22 ; increment variable
d29f: cf 22 ; increment variable
d2a1: cf 22 ; increment variable
d2a3: dd 22 ; set border colour
d2a5: ee 0d 24 09 ff fe 28 05 ff 1f 07 ff 1f 1f ; evaluate expression
d2b3: ef 24 0f 28 01 ; conditional skip
d2b8: fd ; loop back to start of template
d2b9: ee 0e 22 09 ff fe ff bf 05 ff 1f 07 ff 1f 1f ; evaluate expression
d2c8: ef 22 0f ff 02 03 ; conditional skip
d2ce: d6 ff 6f ; include template
d2d1: ee 0e 22 09 ff fe ff fd 05 ff 1f 07 ff 1f 1f ; evaluate expression
d2e0: ef 22 0f ff 02 03 ; conditional skip
d2e6: d6 ff 70 ; include template
d2e9: dd 28 ; set border colour
d2eb: ee 0e 22 09 ff fe ff ef 05 ff 1f 07 ff 1f 1f ; evaluate expression
d2fa: ef 22 0d ff 01 01 ; conditional skip
d300: cd ; return from template inclusion
d301: ee 06 24 fe e8 03 1f ; evaluate expression

TEMPLATE 4e
d308: d0 30 ; set attribute
d30a: d1 24 ; set drawing flags (C024)
d30c: da 40 ff ; move line start
d30f: 00 80 ; pen to (y, x)
d311: 40 00 ; pen to (y, x)
d313: 51 30 ; pen to (y, x)
d315: 60 6f ; pen to (y, x)
d317: 60 99 ; pen to (y, x)
d319: 5a b9 ; pen to (y, x)
d31b: 4f d9 ; pen to (y, x)
d31d: 41 ff ; pen to (y, x)
d31f: d1 00 ; set drawing flags (C024)
d321: 5b 64 ; pen to (y, x)
d323: dc 29 ; textured flood fill
d325: c2 01 ; set room bounding box (preset)
d327: d5 00 a0 5c 86 ; place doorway (type, x, y, z)
d32c: d5 02 8a 5c a0 ; place doorway (type, x, y, z)
d331: e7 01 4a 36 a0 64 ; room exit
d337: e7 02 4a 64 a0 36 ; room exit
d33d: e7 05 4a 64 a0 64 ; room exit
d343: e7 06 4a 64 a0 64 ; room exit

TEMPLATE 4f
d349: d6 ff 5c ; include template
d34c: ee 07 23 23 01 ff 20 1f ; evaluate expression
d354: ef 23 12 ff ff 01 ; conditional skip
d35a: fd ; loop back to start of template

TEMPLATE 50 (empty)

TEMPLATE 51
d35b: ec 03 42 1f ; print text "B"
d35f: d6 ff 52 ; include template

TEMPLATE 52
d362: ec 08 4c 4f 43 4b 45 44 1f ; print text "LOCKED"

TEMPLATE 53
d36b: ec 0b 54 4f 4f 20 48 45 41 56 59 1f ; print text "TOO HEAVY"

TEMPLATE 54
d377: f9 ff c8 ff 64 ; beep (duration, pitch)
d37c: d6 ff 68 ; include template

TEMPLATE 55
d37f: d6 ff 56 ; include template

TEMPLATE 56
d382: d6 ff 68 ; include template
d385: ed 2d ff 60 ff bf ff 14 2b 28 ; define window
d38f: de 2d ; select window
d391: d0 68 ; set attribute
d393: c6 ; set window attributes
d394: ee 12 23 0b fe 8e 7b 02 ff 8d 04 2a 03 ff 20 01 ff 40 1f ; evaluate expression
d3a7: ed 2d 23 ff bf 2c 2b 28 ; define window
d3af: de 2d ; select window
d3b1: d0 78 ; set attribute
d3b3: c6 ; set window attributes
d3b4: ee 0e 22 ff 7b 03 fe 00 01 01 0b fe 8e 7b 1f ; evaluate expression
d3c3: ee 05 22 0a 22 1f ; evaluate expression
d3c9: ef 22 0f 28 01 ; conditional skip
d3ce: c5 ; clear window
d3cf: ef 22 0d 28 03 ; conditional skip
d3d4: d6 ff 57 ; include template
d3d7: ee 07 23 23 01 ff 18 1f ; evaluate expression
d3df: d6 ff 5c ; include template

TEMPLATE 57
d3e2: d2 00 ; set drawing flags (C023)
d3e4: d1 00 ; set drawing flags (C024)
d3e6: fc ff bf 23 ; move line start (y, x operands)
d3ea: ee 06 22 22 01 2a 1f ; evaluate expression
d3f1: ee 08 2e 0b 22 04 ff 08 1f ; evaluate expression
d3fa: cf 22 ; increment variable
d3fc: ee 05 2f 0b 22 1f ; evaluate expression
d402: cf 22 ; increment variable
d404: ee 05 22 0a 22 1f ; evaluate expression
d40a: ef 2e 11 ff 18 06 ; conditional skip
d410: ee 05 2e ff 18 1f ; evaluate expression
d416: f0 22 2e 2f ; draw sprite at cursor (address, width, height)

TEMPLATE 58 (empty)

TEMPLATE 59 (empty)

TEMPLATE 5a
d41a: ef 20 0f ff 06 01 ; conditional skip
d420: cd ; return from template inclusion
d421: ef 20 0f ff 0c 01 ; conditional skip
d427: cd ; return from template inclusion
d428: ef 20 0f ff 0e 01 ; conditional skip
d42e: cd ; return from template inclusion
d42f: ef 20 0f ff 15 01 ; conditional skip
d435: cd ; return from template inclusion
d436: ef 20 0f ff 16 01 ; conditional skip
d43c: cd ; return from template inclusion
d43d: ef 20 11 ff 1b 01 ; conditional skip
d443: cd ; return from template inclusion
d444: d6 ff 5b ; include template

TEMPLATE 5b
d447: ef 20 11 ff 05 05 ; conditional skip
d44d: d5 07 32 6e ac ; place doorway (type, x, y, z)
d452: d5 04 b0 6e 32 ; place doorway (type, x, y, z)
d457: d5 05 32 6e 32 ; place doorway (type, x, y, z)
d45c: ef 20 0d ff 29 05 ; conditional skip
d462: d5 06 32 6e 32 ; place doorway (type, x, y, z)

TEMPLATE 5c
d467: e9 fe 2c c0 ff 08 ; POKE byte
d46d: fb ff bf 23 ; line to (y, x operands)
d471: ec 03 23 1f ; print text "#"
d475: fb ff b7 23 ; line to (y, x operands)
d479: ec 03 24 1f ; print text "$"
d47d: fb ff af 23 ; line to (y, x operands)
d481: ec 03 25 1f ; print text "%"
d485: e9 fe 2c c0 ff 05 ; POKE byte

TEMPLATE 5d
d48b: c1 16 80 82 42 5a ; place object (type, flags, x, y, z)
d491: c1 16 80 6e 42 6a ; place object (type, flags, x, y, z)

TEMPLATE 5e
d497: c1 14 00 64 38 64 ; place object (type, flags, x, y, z)
d49d: c1 15 00 50 42 74 ; place object (type, flags, x, y, z)
d4a3: c1 14 00 82 38 46 ; place object (type, flags, x, y, z)

TEMPLATE 5f
d4a9: 61 2c ; pen to (y, x)
d4ab: d7 ff 80 ; include template (save/restore state)
d4ae: e5 29 ; flag 40: mirror x
d4b0: 4c 7d ; pen to (y, x)
d4b2: d7 ff 7f ; include template (save/restore state)
d4b5: e5 28 ; flag 40: mirror x
d4b7: e4 29 ; flag 20: pen down
d4b9: e2 29 ; flag 04: chain lines
d4bb: da 26 cc ; move line start
d4be: 0d 99 ; pen to (y, x)
d4c0: 53 0d ; pen to (y, x)
d4c2: 6c 40 ; pen to (y, x)
d4c4: 26 cc ; pen to (y, x)
d4c6: 79 cc ; pen to (y, x)
d4c8: bf 40 ; pen to (y, x)
d4ca: 6b 40 ; pen to (y, x)
d4cc: da bf 42 ; move line start
d4cf: a5 0d ; pen to (y, x)
d4d1: 53 0d ; pen to (y, x)
d4d3: e4 28 ; flag 20: pen down
d4d5: e2 28 ; flag 04: chain lines
d4d7: bb 43 ; pen to (y, x)
d4d9: dc ff 0f ; textured flood fill
d4dc: bd 3f ; pen to (y, x)
d4de: dc ff 10 ; textured flood fill
d4e1: c2 07 ; set room bounding box (preset)
d4e3: d5 00 7a 5c 7c ; place doorway (type, x, y, z)
d4e8: d5 02 5c 5c bc ; place doorway (type, x, y, z)

TEMPLATE 60
d4ed: c1 07 00 3c 50 3c ; place object (type, flags, x, y, z)
d4f3: c1 04 00 42 62 42 ; place object (type, flags, x, y, z)
d4f9: c1 03 00 32 62 42 ; place object (type, flags, x, y, z)
d4ff: c1 00 00 42 62 32 ; place object (type, flags, x, y, z)
d505: c1 04 00 40 70 3c ; place object (type, flags, x, y, z)
d50b: c1 04 00 36 70 3c ; place object (type, flags, x, y, z)

TEMPLATE 61
d511: d6 ff 62 ; include template
d514: c1 00 00 32 62 32 ; place object (type, flags, x, y, z)
d51a: c1 04 00 38 7e 38 ; place object (type, flags, x, y, z)

TEMPLATE 62
d520: c1 06 00 3c 50 3c ; place object (type, flags, x, y, z)
d526: c1 04 00 42 5e 42 ; place object (type, flags, x, y, z)
d52c: c1 03 00 32 62 42 ; place object (type, flags, x, y, z)
d532: c1 03 00 42 62 32 ; place object (type, flags, x, y, z)
d538: c1 04 00 40 70 3c ; place object (type, flags, x, y, z)
d53e: c1 03 00 36 70 3c ; place object (type, flags, x, y, z)

TEMPLATE 63
d544: c1 0a 00 32 4a 32 ; place object (type, flags, x, y, z)
d54a: c1 00 00 32 58 32 ; place object (type, flags, x, y, z)
d550: c1 03 00 32 66 32 ; place object (type, flags, x, y, z)

TEMPLATE 64
d556: 02 2a ; pen to (y, x)
d558: 2f 82 ; pen to (y, x)
d55a: 8c 78 ; pen to (y, x)
d55c: 35 0e ; pen to (y, x)
d55e: 20 a8 ; pen to (y, x)
d560: 48 38 ; pen to (y, x)
d562: 49 0e ; pen to (y, x)
d564: 20 ce ; pen to (y, x)
d566: 4a 5e ; pen to (y, x)
d568: 38 0e ; pen to (y, x)
d56a: 20 72 ; pen to (y, x)
d56c: 34 32 ; pen to (y, x)
d56e: 46 0e ; pen to (y, x)
d570: 20 90 ; pen to (y, x)
d572: 34 32 ; pen to (y, x)
d574: 02 0e ; pen to (y, x)
d576: 20 76 ; pen to (y, x)
d578: 34 a6 ; pen to (y, x)
d57a: 2f 0e ; pen to (y, x)
d57c: 20 32 ; pen to (y, x)
d57e: 34 6c ; pen to (y, x)
d580: 04 21 ; pen to (y, x)
d582: c0 ; draw line from line start to pen
d583: 72 46 ; pen to (y, x)
d585: 96 04 ; pen to (y, x)
d587: 09 24 ; pen to (y, x)
d589: 72 3e ; pen to (y, x)
d58b: 5c 05 ; pen to (y, x)
d58d: 0f 20 ; pen to (y, x)
d58f: 50 3a ; pen to (y, x)
d591: 7e 05 ; pen to (y, x)
d593: 0f 20 ; pen to (y, x)
d595: 50 3a ; pen to (y, x)
d597: 6c 05 ; pen to (y, x)
d599: 0b 20 ; pen to (y, x)
d59b: 74 3a ; pen to (y, x)
d59d: 4e 05 ; pen to (y, x)
d59f: 0b 20 ; pen to (y, x)
d5a1: 68 3a ; pen to (y, x)
d5a3: 70 05 ; pen to (y, x)
d5a5: 0c 20 ; pen to (y, x)
d5a7: 56 38 ; pen to (y, x)
d5a9: 4a 05 ; pen to (y, x)
d5ab: 0c 20 ; pen to (y, x)
d5ad: 46 38 ; pen to (y, x)
d5af: 5a 06 ; pen to (y, x)
d5b1: 23 c0 ; pen to (y, x)
d5b3: 94 4a ; pen to (y, x)
d5b5: 42 08 ; pen to (y, x)
d5b7: 21 c0 ; pen to (y, x)
d5b9: 76 46 ; pen to (y, x)
d5bb: 5e 09 ; pen to (y, x)
d5bd: 21 c0 ; pen to (y, x)
d5bf: 92 46 ; pen to (y, x)
d5c1: 98 0a ; pen to (y, x)
d5c3: 0b 20 ; pen to (y, x)
d5c5: 52 3a ; pen to (y, x)
d5c7: 76 0b ; pen to (y, x)
d5c9: 0f 20 ; pen to (y, x)
d5cb: 56 3a ; pen to (y, x)
d5cd: 64 0b ; pen to (y, x)
d5cf: 0c 20 ; pen to (y, x)
d5d1: 44 38 ; pen to (y, x)
d5d3: 94 0b ; pen to (y, x)
d5d5: 0b 20 ; pen to (y, x)
d5d7: 88 3a ; pen to (y, x)
d5d9: 66 0b ; pen to (y, x)
d5db: 0b 20 ; pen to (y, x)
d5dd: 5a 3a ; pen to (y, x)
d5df: 80 0e ; pen to (y, x)
d5e1: 23 c0 ; pen to (y, x)
d5e3: 82 4a ; pen to (y, x)
d5e5: 9a 0f ; pen to (y, x)
d5e7: 21 c0 ; pen to (y, x)
d5e9: 7e 46 ; pen to (y, x)
d5eb: 5e 12 ; pen to (y, x)
d5ed: 09 24 ; pen to (y, x)
d5ef: 36 3e ; pen to (y, x)
d5f1: 36 14 ; pen to (y, x)
d5f3: 0c 20 ; pen to (y, x)
d5f5: 88 38 ; pen to (y, x)
d5f7: a4 14 ; pen to (y, x)
d5f9: 0f 20 ; pen to (y, x)
d5fb: 44 3a ; pen to (y, x)
d5fd: 84 14 ; pen to (y, x)
d5ff: 0f 20 ; pen to (y, x)
d601: 80 3a ; pen to (y, x)
d603: a6 14 ; pen to (y, x)
d605: 0c 20 ; pen to (y, x)
d607: 7a 38 ; pen to (y, x)
d609: 78 14 ; pen to (y, x)
d60b: 0b 20 ; pen to (y, x)
d60d: aa 3a ; pen to (y, x)
d60f: 60 15 ; pen to (y, x)
d611: 23 c0 ; pen to (y, x)
d613: 78 4a ; pen to (y, x)
d615: a2 16 ; pen to (y, x)
d617: 21 c0 ; pen to (y, x)
d619: 66 46 ; pen to (y, x)
d61b: 9c 17 ; pen to (y, x)
d61d: 21 c0 ; pen to (y, x)
d61f: 62 46 ; pen to (y, x)
d621: 8a 18 ; pen to (y, x)
d623: 0c 20 ; pen to (y, x)
d625: 44 38 ; pen to (y, x)
d627: 94 18 ; pen to (y, x)
d629: 0b 20 ; pen to (y, x)
d62b: 68 3a ; pen to (y, x)
d62d: 60 19 ; pen to (y, x)
d62f: 09 24 ; pen to (y, x)
d631: 6e 3e ; pen to (y, x)
d633: 62 1a ; pen to (y, x)
d635: 24 c0 ; pen to (y, x)
d637: 4a 4a ; pen to (y, x)
d639: 3e 1c ; pen to (y, x)
d63b: 02 90 ; pen to (y, x)
d63d: 63 42 ; pen to (y, x)
d63f: 50 1c ; pen to (y, x)
d641: 08 20 ; pen to (y, x)
d643: a6 48 ; pen to (y, x)
d645: 84 1c ; pen to (y, x)
d647: 08 20 ; pen to (y, x)
d649: 9a 48 ; pen to (y, x)
d64b: 84 1d ; pen to (y, x)
d64d: 23 c0 ; pen to (y, x)
d64f: 88 4a ; pen to (y, x)
d651: 82 1e ; pen to (y, x)
d653: 25 c0 ; pen to (y, x)
d655: 76 4a ; pen to (y, x)
d657: 8a 1e ; pen to (y, x)
d659: 21 c0 ; pen to (y, x)
d65b: 9c 46 ; pen to (y, x)
d65d: 5e 1f ; pen to (y, x)
d65f: 08 20 ; pen to (y, x)
d661: 44 48 ; pen to (y, x)
d663: 3a 20 ; pen to (y, x)
d665: 02 90 ; pen to (y, x)
d667: 3e 42 ; pen to (y, x)
d669: 87 23 ; pen to (y, x)
d66b: 21 c0 ; pen to (y, x)
d66d: 7e 46 ; pen to (y, x)
d66f: 5e 23 ; pen to (y, x)
d671: 25 c0 ; pen to (y, x)
d673: 9c 4a ; pen to (y, x)
d675: 94 24 ; pen to (y, x)
d677: 2b 26 ; pen to (y, x)
d679: 68 6a ; pen to (y, x)
d67b: 36 24 ; pen to (y, x)
d67d: 33 00 ; pen to (y, x)
d67f: 94 3c ; pen to (y, x)
d681: 32 24 ; pen to (y, x)
d683: 33 00 ; pen to (y, x)
d685: 94 46 ; pen to (y, x)
d687: 32 24 ; pen to (y, x)
d689: 33 00 ; pen to (y, x)
d68b: 94 50 ; pen to (y, x)
d68d: 32 26 ; pen to (y, x)
d68f: 23 c0 ; pen to (y, x)
d691: 94 4a ; pen to (y, x)
d693: 7e 27 ; pen to (y, x)
d695: 23 c0 ; pen to (y, x)
d697: 8c 4a ; pen to (y, x)
d699: 74 28 ; pen to (y, x)
d69b: 2b 26 ; pen to (y, x)
d69d: 68 6a ; pen to (y, x)
d69f: 4a 28 ; pen to (y, x)
d6a1: 33 00 ; pen to (y, x)
d6a3: 94 3e ; pen to (y, x)
d6a5: 32 28 ; pen to (y, x)
d6a7: 33 00 ; pen to (y, x)
d6a9: 94 4a ; pen to (y, x)
d6ab: 32 28 ; pen to (y, x)
d6ad: 33 00 ; pen to (y, x)
d6af: 94 56 ; pen to (y, x)
d6b1: 32 2a ; pen to (y, x)
d6b3: 23 c0 ; pen to (y, x)
d6b5: 5a 4a ; pen to (y, x)
d6b7: 94 2d ; pen to (y, x)
d6b9: 23 c0 ; pen to (y, x)
d6bb: 60 4a ; pen to (y, x)
d6bd: 8e 2e ; pen to (y, x)
d6bf: 23 c0 ; pen to (y, x)
d6c1: 62 4a ; pen to (y, x)
d6c3: 66 2f ; pen to (y, x)
d6c5: 08 20 ; pen to (y, x)
d6c7: 8e 48 ; pen to (y, x)
d6c9: 68 2f ; pen to (y, x)
d6cb: 08 20 ; pen to (y, x)
d6cd: 8a 48 ; pen to (y, x)
d6cf: 82 2f ; pen to (y, x)
d6d1: 08 20 ; pen to (y, x)
d6d3: 80 48 ; pen to (y, x)
d6d5: 56 2f ; pen to (y, x)
d6d7: 08 20 ; pen to (y, x)
d6d9: 9e 48 ; pen to (y, x)
d6db: 56 2f ; pen to (y, x)
d6dd: 0c 20 ; pen to (y, x)
d6df: 3c 38 ; pen to (y, x)
d6e1: 7a 2f ; pen to (y, x)
d6e3: 0f 20 ; pen to (y, x)
d6e5: 32 3c ; pen to (y, x)
d6e7: 6e 2f ; pen to (y, x)
d6e9: 0f 20 ; pen to (y, x)
d6eb: 34 42 ; pen to (y, x)
d6ed: 74 2f ; pen to (y, x)
d6ef: 0c 20 ; pen to (y, x)
d6f1: 32 38 ; pen to (y, x)
d6f3: 7a 2f ; pen to (y, x)
d6f5: 0b 20 ; pen to (y, x)
d6f7: 32 3a ; pen to (y, x)
d6f9: 74 30 ; pen to (y, x)
d6fb: 23 c0 ; pen to (y, x)
d6fd: 76 4a ; pen to (y, x)
d6ff: 86 31 ; pen to (y, x)
d701: 31 2a ; pen to (y, x)
d703: 8a 36 ; pen to (y, x)
d705: 64 32 ; pen to (y, x)
d707: 29 2e ; pen to (y, x)
d709: 82 3c ; pen to (y, x)
d70b: 6e 32 ; pen to (y, x)
d70d: 08 20 ; pen to (y, x)
d70f: 72 48 ; pen to (y, x)
d711: a4 32 ; pen to (y, x)
d713: 1f 24 ; pen to (y, x)
d715: 72 4e ; pen to (y, x)
d717: aa 33 ; pen to (y, x)
d719: 23 c0 ; pen to (y, x)
d71b: 8e 4a ; pen to (y, x)
d71d: 52 35 ; pen to (y, x)
d71f: 1f 24 ; pen to (y, x)
d721: aa 4c ; pen to (y, x)
d723: 4e 35 ; pen to (y, x)
d725: 1f 24 ; pen to (y, x)
d727: ac 4c ; pen to (y, x)
d729: 38 36 ; pen to (y, x)
d72b: 02 90 ; pen to (y, x)
d72d: 61 42 ; pen to (y, x)
d72f: 60 37 ; pen to (y, x)
d731: 33 00 ; pen to (y, x)
d733: 6e 5a ; pen to (y, x)
d735: 60 37 ; pen to (y, x)
d737: 09 24 ; pen to (y, x)
d739: 78 66 ; pen to (y, x)
d73b: 68 38 ; pen to (y, x)
d73d: 08 20 ; pen to (y, x)
d73f: 72 4a ; pen to (y, x)
d741: 32 3a ; pen to (y, x)
d743: 23 c0 ; pen to (y, x)
d745: 5a 4a ; pen to (y, x)
d747: 60 3b ; pen to (y, x)
d749: 21 c0 ; pen to (y, x)
d74b: 3e 46 ; pen to (y, x)
d74d: 64 3b ; pen to (y, x)
d74f: 23 c0 ; pen to (y, x)
d751: 6a 4a ; pen to (y, x)
d753: 46 3c ; pen to (y, x)
d755: 02 90 ; pen to (y, x)
d757: 73 42 ; pen to (y, x)
d759: 78 3c ; pen to (y, x)
d75b: 02 90 ; pen to (y, x)
d75d: 7f 42 ; pen to (y, x)
d75f: 68 3d ; pen to (y, x)
d761: 23 c0 ; pen to (y, x)
d763: 98 4a ; pen to (y, x)
d765: 70 3e ; pen to (y, x)
d767: 23 c0 ; pen to (y, x)
d769: 72 4a ; pen to (y, x)
d76b: b8 41 ; pen to (y, x)
d76d: 23 c0 ; pen to (y, x)
d76f: 78 4a ; pen to (y, x)
d771: 8e 42 ; pen to (y, x)
d773: 08 20 ; pen to (y, x)
d775: a6 48 ; pen to (y, x)
d777: 84 42 ; pen to (y, x)
d779: 08 20 ; pen to (y, x)
d77b: 9a 48 ; pen to (y, x)
d77d: 84 45 ; pen to (y, x)
d77f: 02 90 ; pen to (y, x)
d781: 64 42 ; pen to (y, x)
d783: 81 46 ; pen to (y, x)
d785: 0c 20 ; pen to (y, x)
d787: 80 38 ; pen to (y, x)
d789: 74 46 ; pen to (y, x)
d78b: 0f 20 ; pen to (y, x)
d78d: 3a 3a ; pen to (y, x)
d78f: 66 46 ; pen to (y, x)
d791: 0c 20 ; pen to (y, x)
d793: 3a 38 ; pen to (y, x)
d795: 6c 46 ; pen to (y, x)
d797: 1f 24 ; pen to (y, x)
d799: 8e 38 ; pen to (y, x)
d79b: 3a 46 ; pen to (y, x)
d79d: 23 c0 ; pen to (y, x)
d79f: 4e 4a ; pen to (y, x)
d7a1: 82 46 ; pen to (y, x)
d7a3: 25 c0 ; pen to (y, x)
d7a5: 4e 4a ; pen to (y, x)
d7a7: 82 47 ; pen to (y, x)
d7a9: 1f 24 ; pen to (y, x)
d7ab: 9c 38 ; pen to (y, x)
d7ad: 98 47 ; pen to (y, x)
d7af: 1f 24 ; pen to (y, x)
d7b1: 9c 38 ; pen to (y, x)
d7b3: 90 47 ; pen to (y, x)
d7b5: 09 24 ; pen to (y, x)
d7b7: 9c 3e ; pen to (y, x)
d7b9: a2 48 ; pen to (y, x)
d7bb: 0c 20 ; pen to (y, x)
d7bd: 98 38 ; pen to (y, x)
d7bf: 74 48 ; pen to (y, x)
d7c1: 0f 20 ; pen to (y, x)
d7c3: 50 3a ; pen to (y, x)
d7c5: 78 48 ; pen to (y, x)
d7c7: 08 20 ; pen to (y, x)
d7c9: 94 48 ; pen to (y, x)
d7cb: 66 49 ; pen to (y, x)
d7cd: 08 20 ; pen to (y, x)
d7cf: c6 ; set window attributes
d7d0: 48 5e ; pen to (y, x)
d7d2: 49 23 ; pen to (y, x)
d7d4: c0 ; draw line from line start to pen
d7d5: 96 4a ; pen to (y, x)
d7d7: 6c ff ; pen to (y, x)
d7d9: ff ; UNKNOWN
d7da: ff ; UNKNOWN
d7db: ff ; UNKNOWN
d7dc: ff ; UNKNOWN
d7dd: ff ; UNKNOWN

TEMPLATE 65
d7de: e9 fe 57 c0 2e ; POKE byte
d7e3: d6 ff 63 ; include template
d7e6: ee 07 2e 2e 02 ff 10 1f ; evaluate expression
d7ee: ce 23 ; decrement variable
d7f0: ef 23 0d 28 01 ; conditional skip
d7f5: fd ; loop back to start of template

TEMPLATE 66
d7f6: d6 ff 67 ; include template
d7f9: 06 00 ; pen to (y, x)
d7fb: be 05 ; pen to (y, x)
d7fd: b9 00 ; pen to (y, x)
d7ff: 02 fb ; pen to (y, x)

TEMPLATE 67
d801: c4 ; line start = pen
d802: e1 29 ; flag 10: relative coords
d804: e2 29 ; flag 04: chain lines
d806: e4 29 ; flag 20: pen down

TEMPLATE 68
d808: bf 45 ; pen to (y, x)
d80a: e0 24 ; print number
d80c: ec 03 20 1f ; print text " "

TEMPLATE 69
d810: ee 05 29 ff 01 1f ; evaluate expression
d816: ee 05 2a ff 02 1f ; evaluate expression
d81c: ee 05 2b ff 03 1f ; evaluate expression
d822: ee 05 2c ff 04 1f ; evaluate expression
d828: ee 05 2d ff 05 1f ; evaluate expression
d82e: ee 0a 22 0a fe 08 c0 01 ff c8 1f ; evaluate expression
d839: ee 05 22 0a 22 1f ; evaluate expression
d83f: fe fe 70 7b fe 28 a0 ff 64 ; block copy (dest, src, length)
d848: e9 fe 75 7b ff 23 ; POKE byte
d84e: e9 fe 7b 7b ff ef ; POKE byte
d854: e9 fe aa 7b 22 ; POKE byte
d859: db fe 1e c0 fe 40 63 ; POKE word
d860: d9 fe 44 61 ; set font
d864: e9 fe 2c c0 2d ; POKE byte
d869: db fe 5b c0 22 ; POKE word
d86e: fe fe 00 bd 22 fe 00 03 ; block copy (dest, src, length)
d876: db fe 5f c0 fe 68 77 ; POKE word
d87d: ed 2c ff 10 ff a7 ff 1c ff 13 ff 61 ; define window

TEMPLATE 6a
d889: de 29 ; select window
d88b: ee 07 20 0a fe 5b c0 1f ; evaluate expression
d893: fe 20 fe 00 bd fe 00 03 ; block copy (dest, src, length)
d89b: ee 04 20 33 1f ; evaluate expression
d8a0: ee 04 21 20 1f ; evaluate expression
d8a5: ee 05 24 ff 63 1f ; evaluate expression
d8ab: e9 fe 70 7b ff 07 ; POKE byte
d8b1: e9 fe 77 7b 28 ; POKE byte
d8b6: e9 fe 79 7b ff 0a ; POKE byte
d8bc: e9 fe 82 7b 28 ; POKE byte
d8c1: e9 fe 84 7b 28 ; POKE byte
d8c6: e9 fe 85 7b 24 ; POKE byte
d8cb: e9 fe 8e 7b ff 8f ; POKE byte
d8d1: e9 fe a4 7b 20 ; POKE byte
d8d6: db fe 58 c0 fe a4 9d ; POKE word
d8dd: e9 fe 5e c0 ff 07 ; POKE byte
d8e3: fe fe 8f 7b fe 99 7b ff 0a ; block copy (dest, src, length)
d8ec: d7 ff 54 ; include template (save/restore state)
d8ef: ed 2b ff 60 ff bf ff 14 2b 28 ; define window
d8f9: de 2b ; select window
d8fb: d0 68 ; set attribute
d8fd: c5 ; clear window
d8fe: d7 ff 56 ; include template (save/restore state)
d901: ed 2b ff 10 ff a7 ff 1c ff 13 28 ; define window
d90c: de 29 ; select window
d90e: ee 05 23 ff 58 1f ; evaluate expression
d914: d6 ff 4f ; include template
d917: fe fe 18 9d fe 8c 9c ff 8c ; block copy (dest, src, length)
d920: d6 ff 6c ; include template
d923: d6 ff 6b ; include template
d926: fd ; loop back to start of template

TEMPLATE 6b
d927: de 2b ; select window
d929: d8 fe f2 7b ; call machine code
d92d: de 29 ; select window
d92f: d1 00 ; set drawing flags (C024)
d931: d2 00 ; set drawing flags (C023)
d933: af 10 ; pen to (y, x)
d935: ee 07 24 0b fe 77 7b 1f ; evaluate expression
d93d: ef 24 0f ff 08 03 ; conditional skip
d943: d7 ff 4c ; include template (save/restore state)
d946: ef 24 0f ff 08 03 ; conditional skip
d94c: d6 ff 4d ; include template
d94f: ef 24 0f fe e8 03 01 ; conditional skip
d956: cd ; return from template inclusion
d957: ee 07 24 0b fe 85 7b 1f ; evaluate expression
d95f: ef 24 0f 28 01 ; conditional skip
d964: cd ; return from template inclusion
d965: ed 2d ff 08 ff b7 ff 09 2a 28 ; define window
d96f: ee 0a 22 0b fe 77 7b 01 ff 50 1f ; evaluate expression
d97a: ef 22 0f ff 57 03 ; conditional skip
d980: d6 ff 71 ; include template
d983: e9 fe 77 7b 28 ; POKE byte
d988: ef 22 12 ff 53 02 ; conditional skip
d98e: de 2d ; select window
d990: ef 22 12 ff 53 03 ; conditional skip
d996: f7 ff 67 ; scroll window
d999: ef 22 12 ff 53 05 ; conditional skip
d99f: f9 ff 0a ff 0a ; beep (duration, pitch)
d9a4: d6 22 ; include template
d9a6: de 29 ; select window
d9a8: ee 07 21 0b fe a4 7b 1f ; evaluate expression
d9b0: ef 21 0f ff 64 03 ; conditional skip
d9b6: d6 ff 95 ; include template
d9b9: ef 21 0f 20 01 ; conditional skip
d9be: fd ; loop back to start of template
d9bf: d6 ff 6c ; include template
d9c2: fd ; loop back to start of template

TEMPLATE 6c
d9c3: e9 fe 24 9d 28 ; POKE byte
d9c8: ee 05 22 ff 7d 1f ; evaluate expression
d9ce: f9 ff 05 fe 58 02 ; beep (duration, pitch)
d9d4: d6 ff 6e ; include template
d9d7: de 2a ; select window
d9d9: c5 ; clear window
d9da: ee 07 22 0b fe 70 7b 1f ; evaluate expression
d9e2: e9 fe 5e c0 22 ; POKE byte
d9e7: ee 07 22 0a fe 58 c0 1f ; evaluate expression
d9ef: fe 22 fe 00 a1 fe e8 03 ; block copy (dest, src, length)
d9f7: fe fe 00 5b fe a4 9d ff 78 ; block copy (dest, src, length)
da00: fe fe a4 9d fe 00 a1 fe e8 03 ; block copy (dest, src, length)
da0a: db fe 58 c0 fe a4 9d ; POKE word
da11: de 29 ; select window
da13: ee 04 20 21 1f ; evaluate expression
da18: e9 fe 5d c0 20 ; POKE byte
da1d: e9 fe a4 7b 20 ; POKE byte
da22: d1 00 ; set drawing flags (C024)
da24: d2 04 ; set drawing flags (C023)
da26: c3 00 00 00 ; set object position
da2a: de 2a ; select window
da2c: d0 20 ; set attribute
da2e: d6 ff 5a ; include template
da31: ef 20 11 ff 1b 02 ; conditional skip
da37: d0 38 ; set attribute
da39: 64 64 ; pen to (y, x)
da3b: d6 20 ; include template
da3d: ee 04 20 21 1f ; evaluate expression
da42: c6 ; set window attributes
da43: eb ff 04 ff 03 ; copy window a to b
da48: c3 00 00 00 ; set object position
da4c: cb ; place room items
da4d: ee 07 2e 0a fe 58 c0 1f ; evaluate expression
da55: fe 2e fe 00 5b ff 78 ; block copy (dest, src, length)
da5c: ee 06 23 fe 8d 7b 1f ; evaluate expression
da63: d6 ff 6d ; include template
da66: db fe 58 c0 2e ; POKE word
da6b: ee 07 22 0b fe 5e c0 1f ; evaluate expression
da73: e9 fe 70 7b 22 ; POKE byte
da78: e9 fe 83 7b ff 08 ; POKE byte
da7e: e9 fe 87 7b ff 04 ; POKE byte
da84: de 2a ; select window
da86: da a7 ef ; move line start
da89: a7 10 ; pen to (y, x)
da8b: c0 ; draw line from line start to pen
da8c: de 29 ; select window
da8e: da a7 ef ; move line start
da91: a7 10 ; pen to (y, x)
da93: c0 ; draw line from line start to pen

TEMPLATE 6d
da94: cf 23 ; increment variable
da96: cf 23 ; increment variable
da98: ef 23 11 fe 99 7b 01 ; conditional skip
da9f: cd ; return from template inclusion
daa0: ee 05 2f 0a 23 1f ; evaluate expression
daa6: ef 2f 0f 28 01 ; conditional skip
daab: fd ; loop back to start of template
daac: db 23 2e ; POKE word
daaf: ee 07 2e 2e 01 ff 14 1f ; evaluate expression
dab7: fd ; loop back to start of template

TEMPLATE 6e
dab8: f9 ff 0c ff 0a ; beep (duration, pitch)
dabd: df 29 ; pause (0 = wait for key)
dabf: f9 ff 04 22 ; beep (duration, pitch)
dac3: ce 22 ; decrement variable
dac5: ce 22 ; decrement variable
dac7: ef 22 11 ff 78 01 ; conditional skip
dacd: fd ; loop back to start of template

TEMPLATE 6f
dace: f8 fe 00 40 fe 40 b7 ; tape: load block (start, length)

TEMPLATE 70
dad5: c9 fe 00 40 fe 40 b7 ; tape: save block (start, length)

TEMPLATE 71
dadc: d0 70 ; set attribute
dade: c5 ; clear window
dadf: 65 68 ; pen to (y, x)
dae1: ec 0c 50 52 45 53 53 20 50 4c 41 59 1f ; print text "PRESS PLAY"
daee: d6 ff 6f ; include template

TEMPLATE 72
daf1: cd ; return from template inclusion
daf2: 64 01 ; pen to (y, x)
daf4: 64 01 ; pen to (y, x)
daf6: 64 01 ; pen to (y, x)
daf8: 64 01 ; pen to (y, x)
dafa: 64 ; data (not decoded: would run into the next template)

TEMPLATE 73
dafb: de 29 ; select window
dafd: d1 00 ; set drawing flags (C024)
daff: d2 00 ; set drawing flags (C023)
db01: 06 14 ; pen to (y, x)
db03: e0 20 ; print number
db05: ec 03 20 1f ; print text " "
db09: ee 07 20 0a fe 58 c0 1f ; evaluate expression
db11: e0 20 ; print number
db13: ec 03 20 1f ; print text " "
db17: ee 07 20 0b fe 5e c0 1f ; evaluate expression
db1f: e0 20 ; print number
db21: ec 03 20 1f ; print text " "
db25: ec 03 20 1f ; print text " "

TEMPLATE 74 (empty)

TEMPLATE 75 (empty)

TEMPLATE 76 (empty)

TEMPLATE 77 (empty)

TEMPLATE 78
db29: e4 29 ; flag 20: pen down
db2b: da bb 3d ; move line start
db2e: ba 42 ; pen to (y, x)
db30: da b6 33 ; move line start
db33: b4 38 ; pen to (y, x)
db35: da b0 29 ; move line start
db38: af 2d ; pen to (y, x)
db3a: da ac 1e ; move line start
db3d: a9 24 ; pen to (y, x)
db3f: da a6 14 ; move line start
db42: a4 1a ; pen to (y, x)
db44: da a1 08 ; move line start
db47: 9e 0f ; pen to (y, x)
db49: da 9a 03 ; move line start
db4c: 9b 00 ; pen to (y, x)
db4e: da bf 45 ; move line start
db51: 9d 00 ; pen to (y, x)
db53: da bf 4f ; move line start
db56: 98 00 ; pen to (y, x)
db58: d6 ff 79 ; include template
db5b: bf 80 ; pen to (y, x)
db5d: d1 00 ; set drawing flags (C024)
db5f: 14 80 ; pen to (y, x)
db61: dc 29 ; textured flood fill
db63: 96 6f ; pen to (y, x)
db65: dc 2a ; textured flood fill

TEMPLATE 79
db67: d1 24 ; set drawing flags (C024)
db69: da 80 80 ; move line start
db6c: 40 00 ; pen to (y, x)
db6e: 00 80 ; pen to (y, x)
db70: 40 ff ; pen to (y, x)
db72: 80 80 ; pen to (y, x)
db74: c2 01 ; set room bounding box (preset)

TEMPLATE 7a
db76: d7 ff 79 ; include template (save/restore state)
db79: 64 64 ; pen to (y, x)
db7b: dc 29 ; textured flood fill

TEMPLATE 7b
db7d: d1 24 ; set drawing flags (C024)
db7f: da 40 00 ; move line start
db82: 80 80 ; pen to (y, x)
db84: 40 ff ; pen to (y, x)
db86: 00 7f ; pen to (y, x)
db88: 18 5a ; pen to (y, x)
db8a: 21 35 ; pen to (y, x)
db8c: 30 11 ; pen to (y, x)
db8e: 3f 01 ; pen to (y, x)
db90: da 30 11 ; move line start
db93: 00 0d ; pen to (y, x)
db95: da 20 35 ; move line start
db98: 00 32 ; pen to (y, x)
db9a: da 00 57 ; move line start
db9d: 17 59 ; pen to (y, x)
db9f: d1 00 ; set drawing flags (C024)
dba1: 02 02 ; pen to (y, x)
dba3: dc 28 ; textured flood fill
dba5: 02 11 ; pen to (y, x)
dba7: dc 28 ; textured flood fill
dba9: 06 38 ; pen to (y, x)
dbab: dc 28 ; textured flood fill
dbad: 02 59 ; pen to (y, x)
dbaf: dc 28 ; textured flood fill
dbb1: 64 64 ; pen to (y, x)
dbb3: dc 29 ; textured flood fill
dbb5: c2 01 ; set room bounding box (preset)

TEMPLATE 7c
dbb7: e5 29 ; flag 40: mirror x
dbb9: d7 ff 86 ; include template (save/restore state)
dbbc: e5 28 ; flag 40: mirror x
dbbe: d7 ff 86 ; include template (save/restore state)
dbc1: d7 ff 82 ; include template (save/restore state)
dbc4: 71 65 ; pen to (y, x)
dbc6: d7 ff 80 ; include template (save/restore state)
dbc9: 6d 51 ; pen to (y, x)
dbcb: dc ff 10 ; textured flood fill
dbce: 81 7a ; pen to (y, x)
dbd0: dc ff 10 ; textured flood fill
dbd3: 82 8c ; pen to (y, x)
dbd5: dc ff 0f ; textured flood fill
dbd8: 6e b4 ; pen to (y, x)
dbda: dc ff 0f ; textured flood fill
dbdd: 82 46 ; pen to (y, x)
dbdf: dc 28 ; textured flood fill
dbe1: 95 7a ; pen to (y, x)
dbe3: dc 28 ; textured flood fill
dbe5: 96 8c ; pen to (y, x)
dbe7: dc 28 ; textured flood fill
dbe9: 8b b1 ; pen to (y, x)
dbeb: dc 28 ; textured flood fill
dbed: d1 24 ; set drawing flags (C024)
dbef: da 60 c1 ; move line start
dbf2: 9a c1 ; pen to (y, x)
dbf4: 86 ff ; pen to (y, x)
dbf6: da 9b c3 ; move line start
dbf9: 9b c5 ; pen to (y, x)
dbfb: 88 ff ; pen to (y, x)
dbfd: d1 00 ; set drawing flags (C024)
dbff: 84 ff ; pen to (y, x)
dc01: dc ff 0f ; textured flood fill
dc04: 46 80 ; pen to (y, x)
dc06: dc ff 0d ; textured flood fill
dc09: d5 00 ae 5c 88 ; place doorway (type, x, y, z)
dc0e: d5 02 88 5c b0 ; place doorway (type, x, y, z)

TEMPLATE 7d
dc13: d6 ff 67 ; include template
dc16: 2d 00 ; pen to (y, x)
dc18: 06 02 ; pen to (y, x)
dc1a: 03 05 ; pen to (y, x)
dc1c: bf 08 ; pen to (y, x)
dc1e: b9 0c ; pen to (y, x)
dc20: b9 05 ; pen to (y, x)
dc22: b8 01 ; pen to (y, x)
dc24: 8f 00 ; pen to (y, x)
dc26: 0b 00 ; pen to (y, x)
dc28: 0c e7 ; pen to (y, x)
dc2a: e2 28 ; flag 04: chain lines
dc2c: bc f8 ; pen to (y, x)
dc2e: 35 08 ; pen to (y, x)
dc30: e2 29 ; flag 04: chain lines
dc32: 88 0f ; pen to (y, x)
dc34: 32 00 ; pen to (y, x)
dc36: e4 28 ; flag 20: pen down
dc38: 04 ec ; pen to (y, x)
dc3a: dc 2b ; textured flood fill

TEMPLATE 7e
dc3c: d6 ff 67 ; include template
dc3f: 0c 18 ; pen to (y, x)
dc41: b5 16 ; pen to (y, x)
dc43: b4 e7 ; pen to (y, x)
dc45: 0b eb ; pen to (y, x)
dc47: da bd 05 ; move line start
dc4a: 07 18 ; pen to (y, x)
dc4c: b8 10 ; pen to (y, x)
dc4e: da bc f9 ; move line start
dc51: bc f9 ; pen to (y, x)
dc53: e4 28 ; flag 20: pen down
dc55: 07 f8 ; pen to (y, x)
dc57: dc 2b ; textured flood fill

TEMPLATE 7f
dc59: d6 ff 67 ; include template
dc5c: 28 00 ; pen to (y, x)
dc5e: 0b 17 ; pen to (y, x)
dc60: 98 00 ; pen to (y, x)
dc62: bf fd ; pen to (y, x)
dc64: 24 00 ; pen to (y, x)
dc66: b8 f0 ; pen to (y, x)
dc68: 9c 00 ; pen to (y, x)
dc6a: 08 0f ; pen to (y, x)
dc6c: e2 28 ; flag 04: chain lines
dc6e: 00 02 ; pen to (y, x)
dc70: 22 fe ; pen to (y, x)

TEMPLATE 80
dc72: e1 29 ; flag 10: relative coords
dc74: ba ef ; pen to (y, x)
dc76: d6 ff 7f ; include template
dc79: e2 29 ; flag 04: chain lines
dc7b: da 13 f2 ; move line start
dc7e: b7 fe ; pen to (y, x)
dc80: bd 00 ; pen to (y, x)
dc82: ba f4 ; pen to (y, x)
dc84: da b3 00 ; move line start
dc87: b9 0c ; pen to (y, x)
dc89: bd 00 ; pen to (y, x)
dc8b: ba f4 ; pen to (y, x)
dc8d: e4 28 ; flag 20: pen down
dc8f: 1c 0d ; pen to (y, x)
dc91: dc ff 0e ; textured flood fill
dc94: e2 28 ; flag 04: chain lines

TEMPLATE 81
dc96: d6 ff 67 ; include template
dc99: b5 15 ; pen to (y, x)
dc9b: 0b fe ; pen to (y, x)
dc9d: 05 fc ; pen to (y, x)
dc9f: 02 fb ; pen to (y, x)
dca1: bf fa ; pen to (y, x)
dca3: bb fc ; pen to (y, x)
dca5: 01 04 ; pen to (y, x)
dca7: e2 28 ; flag 04: chain lines
dca9: 04 02 ; pen to (y, x)
dcab: ba 01 ; pen to (y, x)
dcad: da 04 04 ; move line start
dcb0: be 01 ; pen to (y, x)
dcb2: da 00 02 ; move line start
dcb5: bf 02 ; pen to (y, x)
dcb7: da 00 01 ; move line start
dcba: 00 01 ; pen to (y, x)
dcbc: da be 03 ; move line start
dcbf: be 03 ; pen to (y, x)
dcc1: da 00 02 ; move line start
dcc4: bf 02 ; pen to (y, x)
dcc6: da be 01 ; move line start
dcc9: 00 01 ; pen to (y, x)
dccb: da bb fb ; move line start
dcce: 02 fd ; pen to (y, x)
dcd0: da 6b ee ; move line start
dcd3: e2 28 ; flag 04: chain lines
dcd5: da 52 19 ; move line start
dcd8: 00 03 ; pen to (y, x)

TEMPLATE 82
dcda: e2 29 ; flag 04: chain lines
dcdc: e4 29 ; flag 20: pen down
dcde: da 80 80 ; move line start
dce1: 40 ff ; pen to (y, x)
dce3: 20 c0 ; pen to (y, x)
dce5: 60 41 ; pen to (y, x)
dce7: 80 80 ; pen to (y, x)
dce9: e2 28 ; flag 04: chain lines
dceb: c2 02 ; set room bounding box (preset)

TEMPLATE 83
dced: e2 29 ; flag 04: chain lines
dcef: e4 29 ; flag 20: pen down
dcf1: da 40 ff ; move line start
dcf4: 00 80 ; pen to (y, x)
dcf6: 30 1f ; pen to (y, x)
dcf8: 70 a0 ; pen to (y, x)
dcfa: 40 ff ; pen to (y, x)
dcfc: c2 03 ; set room bounding box (preset)

TEMPLATE 84
dcfe: 6b 54 ; pen to (y, x)
dd00: d7 ff 7f ; include template (save/restore state)
dd03: e4 29 ; flag 20: pen down
dd05: e2 29 ; flag 04: chain lines
dd07: da 7a 53 ; move line start
dd0a: 71 41 ; pen to (y, x)
dd0c: 61 41 ; pen to (y, x)
dd0e: da 86 6b ; move line start
dd11: 90 80 ; pen to (y, x)
dd13: 81 80 ; pen to (y, x)
dd15: d5 02 86 5c b0 ; place doorway (type, x, y, z)

TEMPLATE 85
dd1a: e5 29 ; flag 40: mirror x
dd1c: 5a 36 ; pen to (y, x)
dd1e: d7 ff 80 ; include template (save/restore state)
dd21: d5 00 ae 5c 58 ; place doorway (type, x, y, z)
dd26: e5 28 ; flag 40: mirror x
dd28: d7 ff 83 ; include template (save/restore state)

TEMPLATE 86
dd2b: d7 ff 84 ; include template (save/restore state)
dd2e: e4 29 ; flag 20: pen down
dd30: e2 29 ; flag 04: chain lines
dd32: da 61 41 ; move line start
dd35: 63 3e ; pen to (y, x)
dd37: 8c 3e ; pen to (y, x)
dd39: 8a 40 ; pen to (y, x)
dd3b: 88 41 ; pen to (y, x)
dd3d: 71 41 ; pen to (y, x)
dd3f: da 8c 3e ; move line start
dd42: 8c 42 ; pen to (y, x)
dd44: 88 44 ; pen to (y, x)
dd46: 76 44 ; pen to (y, x)
dd48: 7d 51 ; pen to (y, x)
dd4a: 90 51 ; pen to (y, x)
dd4c: 92 53 ; pen to (y, x)
dd4e: da 78 45 ; move line start
dd51: 7d 50 ; pen to (y, x)
dd53: 91 50 ; pen to (y, x)
dd55: da 8e 4f ; move line start
dd58: 88 4a ; pen to (y, x)
dd5a: 89 43 ; pen to (y, x)
dd5c: 8c 42 ; pen to (y, x)
dd5e: 8a 48 ; pen to (y, x)
dd60: 91 4e ; pen to (y, x)
dd62: 94 51 ; pen to (y, x)
dd64: 93 54 ; pen to (y, x)
dd66: 94 52 ; pen to (y, x)
dd68: 9f 69 ; pen to (y, x)
dd6a: a1 6b ; pen to (y, x)
dd6c: a0 6e ; pen to (y, x)
dd6e: 9e 6c ; pen to (y, x)
dd70: da 9f 6e ; move line start
dd73: 8b 6e ; pen to (y, x)
dd75: 92 7d ; pen to (y, x)
dd77: af 7d ; pen to (y, x)
dd79: ad 80 ; pen to (y, x)
dd7b: 8f 80 ; pen to (y, x)
dd7d: da af 7d ; move line start
dd80: ab 7a ; pen to (y, x)
dd82: a2 73 ; pen to (y, x)
dd84: a0 6f ; pen to (y, x)
dd86: 9d 6f ; pen to (y, x)
dd88: a1 76 ; pen to (y, x)
dd8a: aa 7c ; pen to (y, x)
dd8c: 92 7c ; pen to (y, x)
dd8e: 8c 6f ; pen to (y, x)
dd90: 92 7a ; pen to (y, x)

TEMPLATE 87
dd92: d6 ff 67 ; include template
dd95: da 31 2f ; move line start
dd98: 3a 41 ; pen to (y, x)
dd9a: a4 00 ; pen to (y, x)
dd9c: b7 ee ; pen to (y, x)
dd9e: 1c 00 ; pen to (y, x)
dda0: da a8 03 ; move line start
dda3: be 03 ; pen to (y, x)
dda5: 06 0c ; pen to (y, x)
dda7: ab 00 ; pen to (y, x)
dda9: ba f4 ; pen to (y, x)
ddab: da 19 0a ; move line start
ddae: 07 0a ; pen to (y, x)
ddb0: bb f6 ; pen to (y, x)
ddb2: da 16 08 ; move line start
ddb5: 10 08 ; pen to (y, x)
ddb7: be fc ; pen to (y, x)
ddb9: 07 00 ; pen to (y, x)
ddbb: da be fe ; move line start
ddbe: b8 fe ; pen to (y, x)
ddc0: bf ff ; pen to (y, x)
ddc2: da ba 04 ; move line start
ddc5: 00 04 ; pen to (y, x)
ddc7: 01 03 ; pen to (y, x)
ddc9: b9 00 ; pen to (y, x)
ddcb: bf fd ; pen to (y, x)
ddcd: da be fc ; move line start
ddd0: bf fe ; pen to (y, x)
ddd2: 07 00 ; pen to (y, x)
ddd4: bd fd ; pen to (y, x)
ddd6: e4 28 ; flag 20: pen down
ddd8: e2 28 ; flag 04: chain lines

TEMPLATE 88
ddda: e5 29 ; flag 40: mirror x
dddc: 50 22 ; pen to (y, x)
ddde: d7 ff 80 ; include template (save/restore state)
dde1: d5 00 ae 5c 44 ; place doorway (type, x, y, z)
dde6: e5 28 ; flag 40: mirror x
dde8: d6 ff 7c ; include template

TEMPLATE 89
ddeb: d6 ff 85 ; include template
ddee: e4 29 ; flag 20: pen down
ddf0: e2 29 ; flag 04: chain lines
ddf2: da 70 a0 ; move line start
ddf5: af a0 ; pen to (y, x)
ddf7: 80 ff ; pen to (y, x)
ddf9: da af a1 ; move line start
ddfc: 6f 21 ; pen to (y, x)
ddfe: 30 21 ; pen to (y, x)
de00: 31 1d ; pen to (y, x)
de02: 70 1d ; pen to (y, x)
de04: b2 a1 ; pen to (y, x)
de06: 83 ff ; pen to (y, x)
de08: e4 28 ; flag 20: pen down
de0a: e2 28 ; flag 04: chain lines
de0c: ab a3 ; pen to (y, x)
de0e: dc ff 0f ; textured flood fill
de11: ab 9e ; pen to (y, x)
de13: dc ff 10 ; textured flood fill
de16: b0 a0 ; pen to (y, x)
de18: dc 28 ; textured flood fill
de1a: 46 96 ; pen to (y, x)
de1c: dc 29 ; textured flood fill

TEMPLATE 8a
de1e: d6 ff 88 ; include template
de21: 82 99 ; pen to (y, x)
de23: dc ff 06 ; textured flood fill

TEMPLATE 8b
de26: d6 ff 88 ; include template
de29: 82 99 ; pen to (y, x)
de2b: dc ff 0b ; textured flood fill

TEMPLATE 8c
de2e: 01 8d ; pen to (y, x)
de30: d6 ff 7c ; include template
de33: 82 99 ; pen to (y, x)
de35: dc ff 0b ; textured flood fill

TEMPLATE 8d
de38: d6 ff 82 ; include template
de3b: e4 29 ; flag 20: pen down
de3d: e2 29 ; flag 04: chain lines
de3f: da 60 41 ; move line start
de42: a0 41 ; pen to (y, x)
de44: bf 80 ; pen to (y, x)
de46: 81 80 ; pen to (y, x)
de48: da bf 80 ; move line start
de4b: 80 ff ; pen to (y, x)
de4d: e2 28 ; flag 04: chain lines
de4f: e4 28 ; flag 20: pen down
de51: b4 7f ; pen to (y, x)
de53: dc ff 10 ; textured flood fill
de56: b4 82 ; pen to (y, x)
de58: dc ff 0f ; textured flood fill
de5b: 46 80 ; pen to (y, x)
de5d: dc 29 ; textured flood fill

TEMPLATE 8e
de5f: e4 29 ; flag 20: pen down
de61: e2 29 ; flag 04: chain lines
de63: da 40 ff ; move line start
de66: 12 a2 ; pen to (y, x)
de68: 40 45 ; pen to (y, x)
de6a: 6e a2 ; pen to (y, x)
de6c: 40 fe ; pen to (y, x)
de6e: da 6e a2 ; move line start
de71: bf a2 ; pen to (y, x)
de73: 91 ff ; pen to (y, x)
de75: da bf a2 ; move line start
de78: 91 45 ; pen to (y, x)
de7a: 40 45 ; pen to (y, x)
de7c: e4 28 ; flag 20: pen down
de7e: e2 28 ; flag 04: chain lines
de80: 96 a0 ; pen to (y, x)
de82: dc ff 0e ; textured flood fill
de85: 8c a5 ; pen to (y, x)
de87: dc ff 0f ; textured flood fill
de8a: 64 96 ; pen to (y, x)
de8c: dc ff 08 ; textured flood fill
de8f: c2 04 ; set room bounding box (preset)

TEMPLATE 8f
de91: e2 29 ; flag 04: chain lines
de93: e4 29 ; flag 20: pen down
de95: da 64 64 ; move line start
de98: 71 7d ; pen to (y, x)
de9a: 64 97 ; pen to (y, x)
de9c: 57 7d ; pen to (y, x)
de9e: 64 64 ; pen to (y, x)
dea0: b0 64 ; pen to (y, x)
dea2: bc 7d ; pen to (y, x)
dea4: 71 7d ; pen to (y, x)
dea6: da bc 7d ; move line start
dea9: af 97 ; pen to (y, x)
deab: 64 97 ; pen to (y, x)
dead: e2 28 ; flag 04: chain lines
deaf: e4 28 ; flag 20: pen down
deb1: 70 7d ; pen to (y, x)
deb3: dc 2c ; textured flood fill
deb5: b4 78 ; pen to (y, x)
deb7: dc ff 0e ; textured flood fill
deba: b4 82 ; pen to (y, x)
debc: dc ff 0e ; textured flood fill
debf: c2 05 ; set room bounding box (preset)

TEMPLATE 90
dec1: d6 ff 67 ; include template
dec4: da b5 9b ; move line start
dec7: 1b 4e ; pen to (y, x)
dec9: 89 92 ; pen to (y, x)
decb: a2 3d ; pen to (y, x)
decd: 19 32 ; pen to (y, x)
decf: b8 0f ; pen to (y, x)
ded1: 1d 3b ; pen to (y, x)
ded3: da 27 b5 ; move line start
ded6: 66 b5 ; pen to (y, x)
ded8: 99 4d ; pen to (y, x)
deda: da 27 b3 ; move line start
dedd: af 44 ; pen to (y, x)
dedf: 82 00 ; pen to (y, x)
dee1: e4 28 ; flag 20: pen down
dee3: e2 28 ; flag 04: chain lines
dee5: c2 06 ; set room bounding box (preset)

TEMPLATE 91
dee7: 57 57 ; pen to (y, x)
dee9: d7 ff 87 ; include template (save/restore state)
deec: 50 64 ; pen to (y, x)
deee: d7 ff 7f ; include template (save/restore state)
def1: d6 ff 8e ; include template
def4: 55 69 ; pen to (y, x)
def6: dc ff 0d ; textured flood fill

TEMPLATE 92
def9: e2 29 ; flag 04: chain lines
defb: e4 29 ; flag 20: pen down
defd: da 40 ff ; move line start
df00: 57 ff ; pen to (y, x)
df02: 80 ae ; pen to (y, x)
df04: 80 79 ; pen to (y, x)
df06: 58 29 ; pen to (y, x)
df08: 40 29 ; pen to (y, x)
df0a: 18 79 ; pen to (y, x)
df0c: 18 ae ; pen to (y, x)
df0e: 41 ff ; pen to (y, x)
df10: da 80 79 ; move line start
df13: bf 79 ; pen to (y, x)
df15: da 80 ae ; move line start
df18: bf ae ; pen to (y, x)
df1a: da 56 29 ; move line start
df1d: 98 29 ; pen to (y, x)
df1f: bf 78 ; pen to (y, x)
df21: bf ae ; pen to (y, x)
df23: 97 ff ; pen to (y, x)
df25: da 58 29 ; move line start
df28: 5a 25 ; pen to (y, x)
df2a: 99 25 ; pen to (y, x)
df2c: bf 72 ; pen to (y, x)
df2e: da bf b6 ; move line start
df31: 9a ff ; pen to (y, x)
df33: e2 28 ; flag 04: chain lines
df35: e4 28 ; flag 20: pen down
df37: be a6 ; pen to (y, x)
df39: dc 2d ; textured flood fill
df3b: b9 70 ; pen to (y, x)
df3d: dc ff 07 ; textured flood fill
df40: b9 b0 ; pen to (y, x)
df42: dc ff 06 ; textured flood fill
df45: c2 08 ; set room bounding box (preset)

TEMPLATE 93
df47: d8 fe 1a a4 ; call machine code
df4b: ee 05 20 ff 84 1f ; evaluate expression
df51: d6 ff 94 ; include template
df54: d8 fe 00 b1 ; call machine code

TEMPLATE 94
df58: d0 10 ; set attribute
df5a: ed 2d ff 10 ff af ff 1c ff 10 28 ; define window
df65: de 2d ; select window
df67: c6 ; set window attributes
df68: f7 28 ; scroll window
df6a: ed 2d ff 10 ff 5f ff 1c ff 08 28 ; define window
df75: de 2d ; select window
df77: c6 ; set window attributes
df78: f7 ff 80 ; scroll window
df7b: ed 2d ff 10 ff 27 ff 09 2b 28 ; define window
df85: de 2d ; select window
df87: c6 ; set window attributes
df88: f7 ff 80 ; scroll window
df8b: ed 2d ff 58 ff 27 ff 09 2a 28 ; define window
df95: de 2d ; select window
df97: c6 ; set window attributes
df98: f7 ff 80 ; scroll window
df9b: ed 2d ff a0 ff 27 2d 2b 28 ; define window
dfa4: de 2d ; select window
dfa6: c6 ; set window attributes
dfa7: f7 ff 80 ; scroll window
dfaa: ce 20 ; decrement variable
dfac: ef 20 0d 28 01 ; conditional skip
dfb1: fd ; loop back to start of template

TEMPLATE 95
dfb2: d9 fe 44 61 ; set font
dfb6: e9 fe 2c c0 ff 05 ; POKE byte
dfbc: de ff 01 ; select window
dfbf: d0 36 ; set attribute
dfc1: c5 ; clear window
dfc2: d6 ff 4c ; include template
dfc5: d0 30 ; set attribute
dfc7: c5 ; clear window
dfc8: 0b 3e ; pen to (y, x)
dfca: ec 1f 50 52 45 53 53 20 41 4e 59 20 4b 45 59 20 54 4f 20 4c 4f 41 44 20 50 41 52 54 20 32 20 1f ; print text "PRESS ANY KEY TO LOAD PART 2 "
dfea: df 28 ; pause (0 = wait for key)
dfec: d0 00 ; set attribute
dfee: c5 ; clear window
dfef: fe fe 00 fa fe a4 9d fe 84 03 ; block copy (dest, src, length)
dff9: fe fe 84 fd fe 8e 7b ff 0c ; block copy (dest, src, length)
e002: ee 07 20 0a fe 58 c0 1f ; evaluate expression
e00a: db fe 90 fd 20 ; POKE word
e00f: ee 07 20 0b fe 70 7b 1f ; evaluate expression
e017: e9 fe 92 fd 20 ; POKE byte
e01c: ee 06 2e fe 93 fd 1f ; evaluate expression
e023: ee 06 20 fe b7 9d 1f ; evaluate expression
e02a: ee 05 21 ff 05 1f ; evaluate expression
e030: d6 ff 96 ; include template
e033: d6 ff 6f ; include template

TEMPLATE 96
e036: ee 10 22 0b 20 03 ff 06 01 0a fe 5b c0 02 ff 05 1f ; evaluate expression
e047: ee 05 22 0b 22 1f ; evaluate expression
e04d: e9 2e 22 ; POKE byte
e050: cf 2e ; increment variable
e052: ee 07 20 20 01 ff 14 1f ; evaluate expression
e05a: ce 21 ; decrement variable
e05c: ef 21 0d ff 00 01 ; conditional skip
e062: fd ; loop back to start of template

```