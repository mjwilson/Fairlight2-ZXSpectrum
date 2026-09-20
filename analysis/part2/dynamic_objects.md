# Dynamic objects

By "dynamic objects" I mean to both collectable objects and enemies. These are
held in the same data structure.

Each object has a 6-byte data structure. The first byte holds the room number
which the object is in. The second byte identifies the type of object.

There is a primary copy of the object data at BD00. At the start of the game,
this is copied to D5ED, which is the in-game copy of the data.

```
bd00: 05 25 c0 38 4a 9a ; guard
bd06: 40 0e 20 80 34 8d ; key
bd0c: 37 0e 20 92 56 a0 ; key
bd12: 21 0e 20 40 5c 62 ; key
bd18: 2d 0e 20 80 34 7a ; key
bd1e: 29 0e 20 62 34 74 ; key
bd24: fe 31 2a 00 00 00 ; room fe isn't a room so this object doesn't appear
bd2a: fe 03 00 00 00 00 ; room fe isn't a room so this object doesn't appear
bd30: fe 03 00 00 00 00 ; room fe isn't a room so this object doesn't appear
bd36: fe 03 00 00 00 00 ; room fe isn't a room so this object doesn't appear
bd3c: fe 03 00 00 00 00 ; room fe isn't a room so this object doesn't appear
bd42: 0f 25 c0 34 4a 9a ; guard
bd48: 0f 2e 2c 9c 66 88 ; spiky ball
bd4e: 0f 2f a0 59 38 46 ; disk
bd54: 10 10 80 60 50 46 ; monk
bd5a: 10 25 c0 36 4a 96 ; guard
bd60: 12 0d c0 6a 50 92 ; skeleton
bd66: 14 12 c0 56 4c 40 ; ogre
bd6c: 14 2c 00 60 40 5a ; table
bd72: 14 2d 20 5e 3a 72 ; stool
bd78: 14 2d 20 60 3a 4a ; stool
bd7e: 14 2d 20 56 3a 60 ; stool
bd84: 16 12 c0 70 4c 66 ; ogre
bd8a: 19 2f 80 7e 38 60 ; disk
bd90: 19 2f 80 a6 38 74 ; disk
bd96: 1a 2e 2c 7a 3c 36 ; spiky ball
bd9c: 1a 2e 2c 7a 3c 70 ; spiky ball
bda2: 1b 12 c0 6c 4c 64 ; ogre
bda8: 1f 2c 00 4a 40 66 ; table
bdae: 1f 2c 00 66 40 6a ; table
bdb4: 21 33 00 40 5a 5a ; moving block
bdba: 21 2c 00 54 40 56 ; table
bdc0: 21 10 80 6e 50 7c ; monk
bdc6: 24 2f a0 62 38 4e ; disk
bdcc: 24 2f a0 72 38 a0 ; disk
bdd2: 26 2f a0 9a 38 78 ; disk
bdd8: 26 2f a0 3c 38 50 ; disk
bdde: 28 12 c0 86 4c 70 ; ogre
bde4: 29 12 c0 72 4c 80 ; ogre
bdea: 2c 2e 2c 7e 3c 98 ; spiky ball
bdf0: 2c 2e 2c 7e 3c 7a ; spiky ball
bdf6: 2c 2e 2c 6a 3c 7a ; spiky ball
bdfc: 2c 2e 2c 66 3c 9a ; spiky ball
be02: 2f 10 80 5a 50 5a ; monk
be08: 33 33 00 46 46 32 ; moving block
be0e: 33 33 00 50 3e 32 ; moving block
be14: 33 33 00 5a 38 32 ; moving block
be1a: 36 10 80 6c 50 64 ; monk
be20: 37 12 c0 56 4c 78 ; ogre
be26: 38 12 c0 6e 4c 8e ; ogre
be2c: 3b 0d c0 6a 50 9a ; skeleton
be32: 3d 12 c0 56 4c 8c ; ogre
be38: 3e 2f a0 9a 38 78 ; disk
be3e: 3e 2f a0 9a 38 a0 ; disk
be44: 3f 09 24 64 4c 64 ; bottle
be4a: 3f 10 80 54 50 84 ; monk
be50: 3f 2b 26 62 80 60 ; potion
be56: 3f 2c 00 60 40 5a ; table
be5c: 3f 2d 20 62 3a 4e ; stool
be62: 3f 2d 20 56 3a 5e ; stool
be68: 40 2e 2c 7e 3c 98 ; spiky ball
be6e: 40 2e 2c 7e 3c 7a ; spiky ball
be74: 40 2e 2c 6a 3c 7a ; spiky ball
be7a: 40 2e 2c 66 3c 9a ; spiky ball
be80: 41 0d c0 6a 50 9a ; skeleton
be86: 42 2c 00 54 40 78 ; table
be8c: 42 09 00 5a 4a 7c ; bottle
be92: 44 33 00 66 2a 8c ; moving block
be98: 46 33 00 66 2a 8c ; moving block
be9e: 46 30 2d c8 3c 96 ; magic carpet
bea4: 49 10 80 54 50 84 ; monk
beaa: 4a 0d c0 6e 50 8e ; skeleton
beb0: 4b 0d c0 50 50 50 ; skeleton
beb6: 4d 2c 00 3c 40 46 ; table
bebc: 4d 2d 20 34 3a 4e ; stool
bec2: 4d 2d 20 3a 3a 32 ; stool
bec8: 4e 10 80 7c 4e 6a ; monk
bece: 4f 10 80 7c 68 8a ; monk
bed4: 50 10 80 92 6e 72 ; monk
beda: 51 32 20 8c 5a 8c ; book
bee0: 51 26 80 74 5a a0 ; bat
bee6: ff
```
