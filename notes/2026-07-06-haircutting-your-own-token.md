# Haircutting your own token

The haircut table was easy until it reached SPIRE.

Zero for USDC. Two percent for short-dated tokenised T-bills. Fifteen for tier 1
equities, which is roughly a bad day plus an auction discount. Then the protocol
token, where every incentive points at a generous number and every piece of
history points the other way.

The failure mode writes itself. The day the collateral is needed is the day a
member has defaulted, which is a day the market is stressed, which is a day the
protocol's own token is worth least. Accepting it at face value means the layer
is underwritten by an asset whose price is correlated with the event it is
insuring against.

Thirty-five percent. Still generous, honestly, and it will read as unfriendly to
anyone holding the token expecting it to be treated as cash.

The line I want in the docs is the short one: a clearing layer that accepts its
own token at face value is underwriting itself. If holders dislike the haircut,
that is the mechanism working. The token is a claim on the clearing business, not
a substitute for the collateral the business runs on.
