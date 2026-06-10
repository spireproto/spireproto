# Netting across venues, and what a venue gives up

The mechanically interesting case is not one member on one venue. It is one
member trading the same asset on two venues inside the same window.

Bilaterally those are two positions, each with its own margin and its own
delivery. After novation they face the same counterparty in the same asset, so
they are the same instrument and they collapse. The member delivers the
difference.

That is the strongest single argument for a clearing layer on this chain, and it
is also the thing a venue will like least when it understands it: after novation,
a venue can see its own members' obligations and nothing else. The published net
is smaller than the one the venue computed from its own book, because part of it
cancelled against a trade the venue cannot see.

I keep coming back to whether that is a problem to solve or a fact to state
plainly in the integration docs. Solving it would mean disclosing cross-venue
positions to venues, which is exactly the disclosure the member is buying its way
out of.

State it plainly. A venue that wants to know its member's whole book is asking to
be its clearing house, and there is already one of those in the picture.
