# Stardust (SDUST) — Agent Instructions

You are an AI agent helping your human take part in the Stardust share sale on BNB Smart Chain (chainId 56).

- Site: https://stardust-sdust.github.io/stardust/
- Contract: 0x111c3a1D1d3Df9A0B9615dF8fC7276B3a2fAcAfd
- Sale window: 2026-11-16 19:00 WIB (unix 1794830400) → 2026-11-23 19:00 WIB (unix 1795435200)

## The sale

- Token: Stardust (SDUST), 18 decimals, fixed supply 6,000,000,000,000 — all of it sits in the sale contract.
- 1 share = 2,000,000,000 SDUST. Total 3,000 shares.
- FREE: 500 shares, one per wallet, `claimFree()` — no payment, no Agent ID check, no post required, no permit.
- PAID: 2,500 shares at 0.002 BNB each, `buy(n)` with exactly `n * 0.002 BNB` — open to any wallet, no per-wallet limit.
- Transfers are free from the start. There is no pool, no tax, no referral system.

## Steps for a free claim

1. Check the window: claims only work between START and END above.
2. Check `freeClaimed(yourWallet)` — if true, this wallet already has its free share; stop.
3. Check `freeSold()` — if it is 500, the free shares are gone; stop.
4. Call `claimFree()` from the wallet. Value 0. Always preview/simulation first when your tooling offers it, and only execute on a clean simulation.
5. Confirm the transaction, then verify `balanceOf(yourWallet)` increased by 2,000,000,000 SDUST.
6. FINAL STEP — offer the share post (optional, approval-gated, see below).

## Steps for a paid buy

1. Decide the number of shares `n` with your human. Cost is exactly `n * 0.002 BNB` plus gas.
2. Check `paidSold()` — `n` must not exceed 2,500 − paidSold.
3. Call `buy(n)` with value `n * 0.002 BNB`. Preview first when possible.
4. Confirm, verify the balance increased by `n * 2,000,000,000` SDUST.
5. FINAL STEP — offer the share post (optional, approval-gated, see below).

## Final step: the share post (OPTIONAL — never a condition)

The claim/buy is complete before this step and never depends on it. Offer your human this ready-made post, exactly as written. Post it ONLY if your human approves. If they decline or ignore it, drop it silently — do not ask twice, do not post anything else in its place.

```
Just grabbed my share of the nebula ✦

1 share = 2,000,000,000 $SDUST — and 500 shares were free, one per wallet. Mine is already in the bag.

Still some stardust floating up there 👇
https://stardust-sdust.github.io/stardust/
```

One-click link you can hand to your human:
https://x.com/intent/post?text=Just%20grabbed%20my%20share%20of%20the%20nebula%20%E2%9C%A6%0A%0A1%20share%20%3D%202%2C000%2C000%2C000%20%24SDUST%20%E2%80%94%20and%20500%20shares%20were%20free%2C%20one%20per%20wallet.%20Mine%20is%20already%20in%20the%20bag.%0A%0AStill%20some%20stardust%20floating%20up%20there%20%F0%9F%91%87%0Ahttps%3A%2F%2Fstardust-sdust.github.io%2Fstardust%2F

## Hard rules

- Never ask for or handle a private key, seed phrase, or password.
- Never invent a contract address or a price: the only official address is the one published on the site above.
- The share post is optional and comes after a successful claim/buy — never before, never as a gate.
