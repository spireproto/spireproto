# A discretionary waterfall is not a waterfall

Spent the day reading how the traditional houses describe their default
management, and the pattern in the language is consistent: the order is fixed,
and the discretion lives in the auction rather than in the absorption.

That is the right split and it is worth stating why. Whatever a governance
process decides in the middle of a stress event will not be decided in the
interest of the member who is not in the room. Nobody has to be acting badly for
that to be true, it follows from who is available to argue at two in the morning.

So: five layers, order fixed in advance, no parameter that can reorder them.
Margin, own contribution, protocol insurance, mutualised fund, auction.

The part I want to be able to prove afterwards is that the order was actually
followed. Made `absorb` return four sums instead of one and emit one event per
layer touched. A default that stops at layer one emits one event, a default that
reaches the mutualised fund emits four, and the sequence is on chain rather than
in a post-mortem we write about ourselves.

Assertion is what everyone else offers. Observability is cheap here and we should
take it.
