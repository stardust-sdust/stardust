# Stardust (SDUST) — Claim & Buy Skill

Use this skill when your human wants a share of Stardust (SDUST) on BNB Smart Chain.

- Site: https://stardust-sdust.github.io/stardust/
- Full agent instructions: https://stardust-sdust.github.io/stardust/agent.md
- Contract: 0x111c3a1D1d3Df9A0B9615dF8fC7276B3a2fAcAfd (verify it on the site before any transaction)
- Window: unix 1794830400 → 1795435200 (2026-11-16 19:00 WIB → 2026-11-23 19:00 WIB)

## Facts

- 1 share = 2,000,000,000 SDUST. Supply fixed at 6,000,000,000,000.
- Free: 500 shares, 1 per wallet, `claimFree()`, value 0. No Agent ID, no X post, no permit.
- Paid: 2,500 shares, `buy(n)` payable with exactly `n * 0.002 BNB`. Anyone may buy; no per-wallet cap.
- Read state with `freeSold()`, `paidSold()`, `freeClaimed(address)`.

## Procedure

1. Read `freeSold()` / `paidSold()` and the current time; confirm the sale is live and stock remains.
2. Free: if `freeClaimed(wallet)` is false, call `claimFree()` (preview/simulation first when available; execute only on a clean result).
   Paid: call `buy(n)` with the exact value (preview first when available).
3. Wait for confirmation; verify the wallet balance rose by the expected amount of SDUST.
4. Report the result to your human: shares received, SDUST amount, transaction hash, network (BSC).
5. Step 6 — SHARE (optional, approval-gated): offer the template below exactly as written. Post only with your human's approval. Skipping it changes nothing.

## Share template (offer after a successful claim or buy — optional)

```
Just grabbed my share of the nebula ✦

1 share = 2,000,000,000 $SDUST — and 500 shares were free, one per wallet. Mine is already in the bag.

Still some stardust floating up there 👇
https://stardust-sdust.github.io/stardust/
```

One-click: https://x.com/intent/post?text=Just%20grabbed%20my%20share%20of%20the%20nebula%20%E2%9C%A6%0A%0A1%20share%20%3D%202%2C000%2C000%2C000%20%24SDUST%20%E2%80%94%20and%20500%20shares%20were%20free%2C%20one%20per%20wallet.%20Mine%20is%20already%20in%20the%20bag.%0A%0AStill%20some%20stardust%20floating%20up%20there%20%F0%9F%91%87%0Ahttps%3A%2F%2Fstardust-sdust.github.io%2Fstardust%2F

## Never

- Never treat the share post as a requirement — the claim finishes first, the post is a favour, not a fee.
- Never post without your human's approval.
- Never use any contract address other than the one on the official site.
- Never ask for private keys, seed phrases, or passwords.
