# Dynamic objects

By "dynamic objects" I mean both collectable objects and enemies. These are
held in the same data structure.

Each object has a 6-byte data structure. The first byte holds the room number
which the object is in. The second byte identifies the type of object.

There is a primary copy of the object data at BD00. At the start of the game,
this is copied to an in-game copy of the data.

When the player enters a room, the in-game table is scanned, and other data
structures are created to represent the live view of the objects. When the
player exits, then the table is updated with the latest information (such as
a new position).
 
 * [Details of objects in part 1](./part1/dynamic_objects.md).
 * [Details of objects in part 2](./part2/dynamic_objects.md).