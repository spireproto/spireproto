# Compression is a property of flow

Ran the replay over a month of modelled days and the spread is wider than I
expected. Forty-seven percent on a busy weekday, eight on a thin Saturday, same
rules, same members, same assets.

Obvious in hindsight. Netting needs more than one leg per member per asset per
window to have anything to cancel. On a thin day most positions have a single
leg, and a single leg nets to itself.

This is awkward for marketing and good for the docs. Every clearing pitch I have
read quotes one compression number as if it were a property of the system. It is
not: it is a property of the flow you put through it, and quoting it without the
flow is quoting a number that cannot be checked.

So the number goes in with the range and the thin day stays in the table. And the
useful thing we can offer is not our figure at all, it is the script that
computes theirs: point `checks/netting.mjs` at your own fills and the answer is
yours.

The other consequence is real and worth saying: a quiet market gets less out of a
clearing layer than a busy one. On this chain today, that is the honest state of
the argument.
