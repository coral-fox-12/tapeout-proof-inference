# TapeProof — Verifiable AI Inference on X Layer via TapeOut

**X Layer TapeOut Accelerate** — 100,000 USDT prize pool. Entry for coral-fox-12.
Repo: https://github.com/coral-fox-12/tapeout-proof-inference

## Concept (one line)

An AI inference service whose every answer carries an **on-chain receipt**: the user calls a
TapeOut circuit (its container is the service address), the circuit commits the
prompt/output hash on X Layer, and the web app — hosted on X Layer **DeWEB** — shows the
receipt next to the answer. No account, no API key; whoever holds the circuit NFT owns
the service. Pay-per-call vouchers settle on-chain when TapeOut's escrow ships.

## Why this wins

- **User value first (the #1 judging criterion):** AI answers you can verify — the model,
  the prompt and the output are committed on-chain, so a provider cannot silently swap
  models or fake results. Directly reuses the **Free Model Aggregator** (public, MIT) as
  the inference router.
- **Real TapeOut usage:** a TapeOut **circuit** (logic) + **container** (ERC-6551 account =
  the service address) + **DeWEB** hosting. Not a wrapper — the service *is* the circuit.
- **Commercial model:** free read methods now; paid calls take off-chain vouchers that
  settle on-chain in batches (TapeAPI model, 1% default maintenance contribution,
  provider-settable to 0). Premium routing + private circuits as the paid tier.
- **Existing project, substantial new work:** the aggregator is the base; the TapeOut
  circuit, the container service, the DeWEB deployment and the on-chain attestation are
  all new work completed inside the event window (16 Oct – 7 Dec 2026).

## Eligibility (verified live 18 Nov 2026 from the official page)

- Source: https://web3.okx.com/xlayer/build-x-series
- Prize: **100,000 USDT** — 1st 20,000 ×1, 2nd 10,000 ×5, 3rd 6,000 ×5. Pool may grow.
- Deadline: **submit via the form before 7 Dec 2026, 23:59 UTC** (= 06:59 VN 8 Dec 2026).
  Marked provisional on the page — re-confirm on the event page before submitting.
- Who: individuals and teams, 18+. Online; shortlisted teams attend an **offline Demo Day**
  (travel coverage not stated — flag before committing).
- Vietnam: **not named as restricted** in the terms excerpt read ("Restricted Persons under
  the X Layer Terms of Service are ineligible"). No Vietnam exclusion found.
- Payout: **in stages against agreed development milestones** after eligibility
  verification — not lump-sum. Winners pass identity checks and provide a self-custodial
  wallet (X Layer network). PR support included.
- Submission: Google Form — project description + live URL / contract addresses / circuit
  number + demo video (≤3 min recommended).
- Rules: must use TapeOut circuits, contracts or on-chain data on X Layer, or run on
  X Layer DeWEB. Existing projects allowed only with substantial new work in-window.

## Milestones (see PLAN.md for detail)

| # | Milestone | Target | Done when |
|---|-----------|--------|-----------|
| M1 | TapeOut hello-world on X Layer | ~25 Nov | Circuit taped out + container live; DeWEB site serving the app |
| M2 | Inference as a circuit service | ~1 Dec | Free TapeAPI methods live; on-chain attestation (prompt/output hash) working end-to-end |
| M3 | Paid path + submission | ~6 Dec | Voucher flow wired (escrow if live, else documented); demo video ≤3 min; form submitted |

## Repo layout

- `web/` — the DeWEB app (static front-end; the inference UI + receipt viewer)
- `circuits/` — TapeOut circuit definitions + container wiring (addresses, circuit IDs)
- `contracts/` — X Layer contracts (attestation registry, voucher/escrow adapter)
- `docs/` — PLAN.md, submission checklist, demo script

## Build needs

- X Layer testnet/mainnet access + a fresh experimental wallet (never the main wallet).
- TapeOut canvas + TapeCode (AI dev tool) for circuit creation; TapeAPI docs
  (https://github.com/brucelanlan/tapeapi — v3.0.0, 2026-11-06).
- Free Model Aggregator as the inference router (already built).
- Demo video ≤3 min + Google Form submission (browser step — parent arranges).

## Status

- [x] Eligibility verified (official page, 18 Nov 2026)
- [x] Repo created + scaffold pushed
- [ ] M1 — circuit + container + DeWEB
- [ ] M2 — inference service + attestation
- [ ] M3 — paid path + video + form submit (by 7 Dec 23:59 UTC)
