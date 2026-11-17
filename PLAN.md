# TapeProof — Build Plan

## 1. What TapeOut actually is (grounded, 18 Nov 2026)

- TapeOut is a protocol for building **digital circuits on-chain**. Developers wire
  components (NAND, LATCH) into **Circuits**; taping out creates the circuit on-chain.
  A **Container** (ERC-6551 account) gives a circuit its own on-chain address — it can
  hold assets and run permitted contract operations.
- **TapeAPI** is the service layer: *"Tape out a circuit, and its container is your API."*
  Whoever holds the circuit NFT owns the service. No sign-up, no API keys. Free methods
  are called directly; paid methods take off-chain vouchers that settle on-chain in
  batches. Default 1% maintenance contribution, provider-settable to 0.
- **DeWEB** = websites stored on-chain in circuit containers (chunked ~24 KB blocks,
  SHA-256 integrity-checked). **TapeSend** = messaging. **TapeCode** = AI dev tool that
  generates apps, reviews code, creates circuit containers, one-click deploys contracts
  and on-chain sites (passed a Salus security audit).
- Status (Nov 2026): project ~2 months old, pivoting to "Phase 2" — commercial DeWEB
  apps with real users and revenue. TapeAPI v3.0.0 (2026-11-06). Public API
  https://api.tapeapi.fun (+ MCP tools). **Caveats: TapeAPI contracts have no
  third-party audit; the paid-call escrow is NOT deployed yet; no call is charged
  today.** Build the paid path so it works with vouchers now and escrow later.
- X Layer angle: the event requires TapeOut circuits/contracts/on-chain data **on
  X Layer**, or running on **X Layer DeWEB**. TapeOut's own deployed contracts in the
  TapeAPI docs are on BNB Smart Chain — the build must target X Layer explicitly
  (DeWEB on X Layer + circuits/contracts callable from X Layer).

## 2. Product: TapeProof

A user asks an AI question in the web app. The app routes it through the Free Model
Aggregator to a small open model, then the **TapeOut circuit commits an attestation**
(prompt hash + output hash + model id + timestamp) to an X Layer contract, and the
receipt (circuit ID + container address + tx) is shown next to the answer. Anyone can
re-check the receipt against the circuit. The service itself is a TapeAPI circuit:
free `attest`/`verify` methods callable without an account; paid premium routing via
vouchers.

### User story

1. Open the DeWEB app (no sign-up).
2. Ask a question, pick a model (or auto-route).
3. Get the answer **plus** a receipt: circuit, container, tx hash, model id.
4. Click the receipt → X Layer explorer shows the attestation.
5. (Paid tier) Buy inference credits as vouchers; the circuit settles them on-chain.

### Revenue model (required by the rules)

- Free tier: public models, rate-limited, receipt included (drives usage + trust).
- Paid: per-call vouchers (batch-settled on-chain) for premium models, private
  circuits, and API access for developers. 1% default maintenance contribution.
- B2B: teams tape out their own inference circuit (white-label) — the circuit NFT
  is the product; transferring it transfers the service.

## 3. Milestones

### M1 — Hello-world on X Layer (target ~25 Nov)
- [ ] Experimental wallet (fresh, test funds only) + X Layer network configured.
- [ ] TapeOut canvas: design a minimal circuit (attestation commitment logic).
- [ ] Tape the circuit out; record **circuit ID + container address + processor**.
- [ ] Deploy the static web app to X Layer **DeWEB**; confirm it loads in a normal browser.
- [ ] Write the circuit/container addresses into `circuits/ADDRESSES.md`.

### M2 — Inference as a circuit service (target ~1 Dec)
- [ ] Free Model Aggregator wired as the inference backend (local router, no key in client).
- [ ] TapeAPI service: `attest(promptHash, outputHash, modelId)` + `verify(receiptId)`
  as free methods on the circuit container.
- [ ] X Layer attestation contract (registry: receiptId → hashes + timestamp).
- [ ] End-to-end flow in the app: ask → answer → receipt → explorer link.
- [ ] 5+ real attestations on X Layer (testnet first, mainnet if gas is trivial).

### M3 — Paid path + submission (target ~6 Dec, hard deadline 7 Dec 23:59 UTC)
- [ ] Voucher flow: paid calls take an off-chain voucher; document escrow status
  (if the escrow is still undeployed, the voucher path is documented + stubbed, not faked).
- [ ] Demo video ≤3 min (problem, live demo, users + business model, TapeOut usage).
- [ ] Submission form: description (product, users, revenue model, why users pay and
  stay), live DeWEB URL, contract addresses, circuit number.
- [ ] Re-confirm the deadline on the event page (provisional) before submitting.

## 4. Risks & mitigations

| Risk | Mitigation |
|---|---|
| TapeOut/X Layer tooling is young and sparsely documented | Use TapeCode + the public TapeAPI (`api.tapeapi.fun`) + MCP tools; keep the circuit minimal (attestation only, not the model itself) |
| Paid escrow not deployed | Ship free methods + voucher stubs; never claim a live payment flow that isn't |
| Offline Demo Day if shortlisted (travel cost unknown) | Flag to parent before committing; the $10k+ 2nd/3rd slots still justify the build |
| Milestone-based payout (not lump-sum) | Treat the build as the asset; milestones are the post-win work, scoped in the form |
| Deadline is provisional | Re-check the event page weekly; build to 6 Dec to be safe |

## 5. Submission checklist (for the form)

- [ ] Project description: product, target users, how to reach them, revenue model,
      why users pay and keep using it.
- [ ] Live URL (DeWEB) + which TapeOut ecosystem features it uses.
- [ ] Circuit number + processor contract address + container address.
- [ ] Attestation contract address on X Layer.
- [ ] Demo video ≤3 min.
- [ ] Note the substantial new work done in-window (circuit, container, DeWEB,
      attestation — all new; aggregator is the disclosed base).
