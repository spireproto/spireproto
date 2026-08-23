# A proof that leaks the book

First version of the solvency proof published the whole position table each
window. It is trivially checkable, which was the goal, and it is also a complete
disclosure of every member's exposure, which is a product nobody would buy.

The whole point of clearing through a central counterparty, from a member's
perspective, is that its book stops being visible to the people it trades with.
Publishing it for verification hands back exactly what novation took away.

Merkle commitment over per member positions and collateral. The aggregate is
public, coverage is a single number anyone can read, and a member can prove its
own line without any other line being disclosed.

Wrote the sentence I want to keep: a proof that reveals every member's position
is not a transparency feature, it is a leak with a nice name.

What the commitment still does not do is tell anyone whether the margin rates are
adequate. That is a judgement, and no root can launder a judgement into a fact.
It removes the separate and much stupider risk of the numbers being misreported,
which is the failure mode that should not exist on a chain at all.
