# Part 1 to part 2 handover

When passing from part to part 2, there is special code to hand over the objects
you are carrying. This is critical for completing part 2, as the magic wand has to be
carried over.

Note that this code seems to be buggy, in that the behaviour changes if you restart
during part 2. For example, directly after entering part 2, you can drop the sword in 
the starting room, leave and re-enter the room, and it will still be the sword.

But if you die and part 2 restarts, the sword will turn into a skeleton.

This also seems to stop the magic wand from being used to unlock the final door.

## Worked example

Let's say you are holding the key from the opening room, the magic wand, and the sword (in slots 1-3 respectively).
Before loading part 2, the game copies the details of the objects you are carrying to FA00.

So the details of the key are held from FA00, the wand from FA14, and the sword from FA28.

Additionally, the object types are recorded as follows:

* FD93 = 0E
* FD94 = 29
* FD95 = 31

(FD96, FD97 would be used for other objects if we were holding them in the remaining slots.)

On arriving in part 2, the data is reinstated as follows:

* Copy the data at FA00 to 9DA4 (just reinstating the previous values where they were before)
* Take additional copies for use on restart
* Update the dynamic object list with the items you are carrying

The dynamic object list for part 2 contains 5 slots for the items you carried over from part 1
(entries 07-0B).

So the objects you are carrying end up with ids

* 07 (key)
* 08 (magic wand)
* 09 (sword)

The game then scans through your objects, and if it finds the magic wand, it sets that object's
id as the one which will unlock the final locked door in the game.

However a bug means that if the game restarts during part 2, the object ids get reset to the ids
they had during part 1. So these are now

* 06 (still a key)
* 49 (points to a skeleton)
* 48 (also a skeleton)

You can see this by noting that:

* before dying in part 2 - you can drop the wand and sword in a room, leave and re-enter, then pick them up
* after dying in part 2 and restarting - if you try it, they will turn into skeletons

This is different in the 128K version of the game:

* they turn into a table and chair, not skeletons
* this happens as soon as you enter part 2 - you don't need to die to trigger a restart