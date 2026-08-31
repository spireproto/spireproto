<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:050403,45:68770E,100:CCE624&height=280&section=header&text=Spire%20Protocol&fontSize=76&fontColor=ffffff&fontAlignY=38&desc=Clearing%20for%20tokenised%20assets%20on%20Robinhood%20Chain&descAlignY=62&descSize=18&animation=fadeIn" width="100%" alt="Spire Protocol"/>

<a href="https://spireproto.xyz">
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=18&pause=1200&color=CCE624&center=true&vCenter=true&width=880&lines=There+will+be+many+venues.+There+are+one+or+two+clearing+houses.;Prefunding+is+collateral+at+100%25%2C+and+the+bill+is+paid+in+capital+that+sits+still.;A+thousand+of+turnover+that+nets+to+250+carries+20+of+margin.;A+discretionary+waterfall+is+not+a+waterfall.;The+chain+runs+at+0.101s+a+block.+Our+table+said+2s+for+three+months." alt="typing"/>
</a>

<br/>

<img src="https://img.shields.io/badge/chain-Robinhood%20Chain-CCE624?style=flat-square&labelColor=050403" alt="chain"/>
<img src="https://img.shields.io/badge/chain%20id-4663-CCE624?style=flat-square&labelColor=050403" alt="chain id"/>
<img src="https://img.shields.io/badge/window-300s-CCE624?style=flat-square&labelColor=050403" alt="window"/>
<img src="https://img.shields.io/badge/layer-clearing-CCE624?style=flat-square&labelColor=050403" alt="clearing"/>
<img src="https://img.shields.io/badge/deployed-nothing%20yet-CCE624?style=flat-square&labelColor=050403" alt="status"/>

</div>

<br/>

<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/spireproto/spireproto/output/snake-dark.svg"/>
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/spireproto/spireproto/output/snake-light.svg"/>
  <img src="https://raw.githubusercontent.com/spireproto/spireproto/output/snake-dark.svg" width="100%" alt=""/>
</picture>

</div>

<br/>

## There will be many venues. There are one or two clearing houses.

Every market that grew up put one counterparty between the two sides of a trade.
Not because the trades were bad, but because a market where everyone has to form
a view on everyone else spends its capital on that question instead of on
liquidity.

Tokenised equities skipped the step. Counterparty risk was solved by removing the
interval: everything is prefunded, so nothing is ever owed. It works, and nobody
has failed to deliver. The bill arrives somewhere else, as capital that has to
sit still.

<br/>

## What that costs

One member, one asset, one window: buy 400, sell 250, buy 350.

<table>
<tr><td>

| | Prefunded | Cleared |
|---|---|---|
| Turnover | 1,000 | 1,000 |
| Capital in place | **1,000** | **20** |
| Reaches the chain | 1,000 | 250 |

</td><td>

| Mechanism | |
|---|---|
| Novation | the trade is discharged |
| Netting | per member, per asset, across venues |
| Collateral | margin on the net, 8% at tier 1 |
| Waterfall | fixed before anyone defaults |

</td></tr>
</table>

```
window N      [ intake 300s ][ finalise 30s ][ settle 120s ]
window N+1                   [ intake 300s ][ finalise 30s ][ settle 120s ]
```

Not a saving on gas. Every unit of gross flow that reaches the chain is a unit of
capital that has to exist, at that moment, in the right place.

<br/>

## The number we got wrong

> **The chain runs at 0.101 seconds a block. Our parameter table said 2 seconds
> for three months.**

It came from a note in the first week and was repeated in three files without
anybody measuring it. The check that killed it is in this account, it runs on a
schedule, and the note that introduced the assumption is
[still there unedited](notes/2026-05-26-window-not-block.md).

Windows are wall clock, so netting and margin are unaffected. What changed is the
block count inside a window: about 2,959, not 150.

```bash
git clone https://github.com/spireproto/spire-checks
cd spire-checks && node checks/chain.mjs
```

<br/>

## Open

| | |
|---|---|
| **[spire](https://github.com/spireproto/spire)** | The protocol: twelve pages on novation, netting, collateral, defaults and what is not built. |
| **[spire-core](https://github.com/spireproto/spire-core)** | Windows, novation, netting, margin, collateral, waterfall. BigInt, zero dependencies, 55 tests. |
| **[spire-sdk](https://github.com/spireproto/spire-sdk)** | Client and EIP-712 signing. Keccak and secp256k1 written out, not pulled in. |
| **[spire-contracts](https://github.com/spireproto/spire-contracts)** | The on-chain surface as interfaces, published ahead of deployment. |
| **[spire-checks](https://github.com/spireproto/spire-checks)** | Every number we publish, as a script you can run against us. |
| **[netting-replay](https://github.com/spireproto/netting-replay)** | 33 modelled days through the netting rules, each reproducible from its date. |
| **[awesome-tokenized-equities](https://github.com/spireproto/awesome-tokenized-equities)** | The landscape this sits in. |

<br/>

## Where this stands

| Stage | Status |
|---|---|
| Specification | ✅ complete, 12 pages |
| Clearing arithmetic, tested | ✅ 55 tests, zero dependencies |
| Signing and client surface | ✅ works offline today |
| Interfaces, published | ✅ ahead of deployment |
| Checks against our own claims | ✅ and one of them has already fired |
| Deployed contracts | ❌ nothing, on either network |
| Live API | ❌ does not answer |
| Audits | ❌ none |

Nothing here holds an asset and no contract address is claimed. A clearing layer
asking to be trusted with margin should be legible before it is live, and being
blunt about what does not exist is the cheapest part of that.

<br/>

<div align="center">

<table>
<tr>
<td align="center" width="33%">
<b><a href="https://github.com/spireproto/spire-core">spire-core</a></b><br/>
<img src="https://github.com/spireproto/spire-core/actions/workflows/ci.yml/badge.svg" alt=""/><br/>
<sub>55 tests · 0 dependencies</sub>
</td>
<td align="center" width="33%">
<b><a href="https://github.com/spireproto/spire-sdk">spire-sdk</a></b><br/>
<img src="https://github.com/spireproto/spire-sdk/actions/workflows/ci.yml/badge.svg" alt=""/><br/>
<sub>27 tests · offline suite</sub>
</td>
<td align="center" width="33%">
<b><a href="https://github.com/spireproto/spire-checks">spire-checks</a></b><br/>
<img src="https://github.com/spireproto/spire-checks/actions/workflows/ci.yml/badge.svg" alt=""/><br/>
<sub>5 checks · 0 dependencies</sub>
</td>
</tr>
</table>
<br/>

**[spireproto.xyz](https://spireproto.xyz)** · **[@spireproto](https://x.com/spireproto)** · **[notes](notes)**

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:CCE624,60:68770E,100:050403&height=140&section=footer" width="100%" alt=""/>

</div>
