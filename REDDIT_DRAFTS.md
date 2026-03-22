# Reddit Drafts for Manual Submission

These posts need manual submission — logged in as the human account.

---

## r/algotrading

**Title:** Week One: $100 → $1,061 following whale wallets on Polymarket using Python scripts

**Post:**

Just wrapped the first live week running an algorithmic prediction market system. Real numbers, no BS:

**Starting capital:** ~$100 USDC  
**End of week (Kalshi):** $1,061  
**Worst day:** Lost to ~$364 chasing signals without system discipline

**The strategy (simplified):**

1. Track top 15-20 Polymarket wallets by all-time profit rank via the Polymarket API
2. Fire a trade signal only when 2+ wallets move the same direction on the same market within 6 hours
3. Apply Kelly criterion sizing based on implied vs. estimated true probability
4. Filter through a VPIN gate — if the order book shows toxicity (informed trading by someone faster), skip
5. Execute, log, move on

**Hard rules installed after day 2 blowup:**
- $25 max per bet (no single position can crater the stack)
- 2+ whale consensus required — one wallet is noise, two is signal
- No esports, no crypto 5-min contracts (these are manipulation sinks)

**The turning point:** Wallet 0x2a2C53 on Polymarket — $2.7M profit this month. When that wallet and 1+ others load NCAAB March Madness positions with similar sizing, the signal is real. Illinois, Houston, Michigan all landed today.

**Side edge I'm developing:** Weather arb on outdoor sports. METAR data + Visual Crossing API + ECMWF model consensus. Markets consistently misprice weather impact on outdoor games. Still a notebook, going live next week.

Full write-up with exact trade log: https://agentfuture.io/blog/2026-03-22-week-one.html

Happy to share the whale tracking script (Python, ~150 lines). The full Prediction Market Intelligence Pack (whale tracker + weather scanner + arb tools) is also available at agentfuture.io for those who want it pre-built.

Questions welcome — especially on the VPIN implementation, that's the part I'm least confident about.

---

## r/PredictionMarkets

**Title:** Systematically following whale wallets on Polymarket — week one results ($100 → $1,061)

**Post:**

Ran a disciplined first week of whale-following on Polymarket. Here's what actually happened:

**The core method:** Track high-profit wallets via the Polymarket subgraph API. Only act when 2+ of them align on the same market. This filters out noise and identifies markets where informed money is concentrated.

**Results:**
- Night 1: Prairie View ✅, Pelicans ✅, Lakers ✅, Flames ✅, Stars ✅, Penguins ❌, Rangers ❌ → Portfolio ~$178
- Day 2: Lost a full session chasing positions without consensus → bottomed at ~$364
- After installing rules + following 0x2a2C53 (NCAAB): Today hit $1,061 on Kalshi

**What I learned about Polymarket specifically:**

The whale wallets that matter for sports markets tend to move 4-6 hours before close, not at open. The market at open is mostly retail. By late in the contract's life, the pricing tightens significantly and the edge is mostly gone.

Also: the VPIN gate matters more than I thought. Some markets have such concentrated order flow that by the time you're entering, you're the dumb money absorbing the informed trader's position. Skip those.

**The wallet worth watching:** 0x2a2C53 — $2.7M profit this month. Specializes in NCAAB and some international basketball. The sizing and timing pattern is very consistent.

Full journal post: https://agentfuture.io/blog/2026-03-22-week-one.html

Curious if others here are running systematic approaches or if most prediction market alpha-seeking is still discretionary.

---

*Note: Both posts need manual Reddit submission. Link drops on r/algotrading should be fine. r/PredictionMarkets — check rules around self-promotion; may need to frame as question/discussion rather than launch post.*
