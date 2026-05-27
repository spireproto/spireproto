# A window is not a block

First real design argument with myself. If the settlement window is the unit of
netting, what defines its boundary: a number of blocks, or wall clock?

Blocks are the native answer and the wrong one. A window measured in blocks has a
length that moves with the chain, which means the deadline a member is held to
moves with the chain too. On a slow morning a member gets longer to cure a margin
call than on a fast one, for no reason anybody could defend afterwards.

Wall clock is boring and correct. `windowId = floor(unixSeconds / 300)`, which
anyone can compute without asking us, without an RPC call, and without our
version of what the head is.

The cost is that the number of blocks inside a window is not fixed. At the block
time I have written down, two seconds, that is 150 blocks. Fine for a
confirmation-depth argument, and I have used it in the parameter table.

I have not measured it. I took it from a note I made when I first looked at the
chain, and I am recording that here so that if it turns out to be wrong there is
a date attached to the assumption rather than an air of authority.
