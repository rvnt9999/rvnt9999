<div align="center">

<img src="https://launcher.ohshii.io/logos/ohshii.svg" width="110" alt="OhShii" />

# Ravenith

### Core developer @ [OhShii Labs](https://ohshii.io)

**A community-governed DAO on the Internet Computer, built on proof of personhood, Sybil
resistance, and governance that is expensive to capture.**

[![Website](https://img.shields.io/badge/ohshii.io-0A0818?style=for-the-badge&logo=internetcomputer&logoColor=29ABE2)](https://ohshii.io)
[![Docs](https://img.shields.io/badge/Documentation-0A0818?style=for-the-badge&logo=markdown&logoColor=white)](https://ohshii.io/docs)
[![X](https://img.shields.io/badge/@ohshiidao-0A0818?style=for-the-badge&logo=x&logoColor=white)](https://x.com/ohshiidao)

</div>

---

## What I work on

OhShii started as a launch framework and that is still most of what it does today, but the
framework is the foundation, not the goal. The goal is a DAO owned by its community that uses
its own governance and treasury to get useful things built on the Internet Computer.
Everything below is the machinery for that: a DAO that decides where its own resources go has
to be hard to capture first.

**[OhShii Launcher](https://launcher.ohshii.io)** bootstraps a DAO and the community that
governs it. Voting weight is quadratic and capped per identity, behind a proof of personhood
gate (World ID, DecideID). Without Sybil resistance, quadratic voting is weaker than linear:
an attacker splits one wallet into many and beats the square root.

Contributions stay in escrow for the length of the campaign. If it fails everyone is refunded
automatically, and nobody has to decide to pay it back. If it succeeds, control passes to the
campaign's own governance canister and OhShii is dropped as a controller. No human step, no
way to undo it.

Allocation is capped too, not just influence: how many tokens one identity can take out of a
campaign is bounded by tier, set by verification status and OHSHII voting power. More capital
raises the ceiling but never removes it, and a wallet that stops voting on ONS proposals drops
to a lower one until it votes again. Allocated tokens arrive in
a vesting lock that already votes in the campaign DAO while it is still vesting, so governance
starts at distribution instead of after it.

**The code upgrades by vote.** A new version of a DAO's canister is proposed on-chain as a
wasm. Before voting, anyone can rebuild it from source and check the hash against what was
uploaded, so the vote is cast on verified bytes instead of on a changelog. If it passes, the
canister upgrades itself. No admin key, no multisig, no team that can ship an update, nothing
to compromise: the only route from source to production runs through a vote. This is how
OhShii's own governance works, and how every DAO launched on it works.

**Capture resistance.** A capital driven takeover always looks the same: acquire decisive
voting weight cheaply while the token trades low, then vote the treasury out. The damped voting
curve above is the first obstacle. Behind it, thresholds follow a two axis Normal / Critical
model, and grandfathering stops a rule change from reaching a vote already in flight. None of
it makes a takeover impossible, it makes it slow, expensive and visible.

**A token that already exists can become a DAO.** No launch required. OhShii deploys a
governance canister for it, and from then on the community runs voting, locks and proposals
from the interface, with no dependency on OhShii or ONS. Hand your dapp's canisters to it and
holders vote on how the dapp evolves. Hand over the ledger, archive and index canisters too
and they govern the token itself.

**Not a replacement for the SNS, and not a fork of it.** OhShii is an independent
implementation, written from scratch in Rust. The SNS is DFINITY's own framework and it is
genuinely battle tested: years of real launches behind it, NNS-level oversight, and tooling
hardened by production use. OhShii is not a lighter SNS. It is a different design with
different trade-offs, and the two diverge structurally rather than by configuration.

| | SNS | OhShii |
|---|---|---|
| To start | An NNS neuron, and an NNS proposal where the community votes on your tokenomics and can reject them | No proposal and no external vote on whether a project may proceed; eligibility is objective and enforced in code |
| Canisters deployed | Six, automatically: Governance, Root, Swap, Ledger, Index and Archive | One. A single SONS governance canister per DAO carries proposals, voting, treasury, locks and vesting; the token keeps its own standard ledger and index |
| Canister control | Passes through NNS Root, then SNS Root becomes sole controller | The DAO's governance canister answers to itself |
| Launch | Eleven stages, with minimum participant counts and participation floors to get right the first time | An LGE, refunded automatically if it does not complete |
| Voting | Stake weighted, with dissolve delay and age bonuses, so control tracks tokens closely | Quadratic behind a personhood gate, so influence does not track capital in a straight line |

A project that wants the NNS-backed framework should use the SNS. OhShii exists for smaller
projects that want an on-chain DAO without that ceremony.

**[OhShii Locker](https://locker.ohshii.io)** handles locking and vesting for ONS, SONS
entities, imported DAO governance canisters and third party tokens alike, as a one time unlock
on a chosen date or a linear vesting plan. Every operation is immutable and verifiable on chain.

**[Explorer / Atlas](https://explorer.ohshii.io)** is wallet and token analytics for the IC,
and the deliberate exception to everything above. They read the chain through external servers,
because doing that indexing inside canisters costs more than a purely statistical tool is
worth. So they stay outside the DAO's control, as OhShii community applications rather than
DAO ones. They hold no funds and carry no core logic. Custody and governance are on-chain and
DAO-governed, statistics are not.

**Cross-Chain Gateway** brings Bitcoin and Solana into the ICP ecosystem, with no custodians
and no traditional bridges. Bitcoin is minted as ckBTC through DFINITY's native chain-key
minter and redeemed back to native BTC by burning it.

The Solana side is not ours. Chain-key Solana does not exist natively on the Internet Computer
yet, and Solana works here because [Menese Protocol](https://github.com/Menese-Protocol/MeneseSDK-V0)
built it: their chain-key execution layer signs and broadcasts Solana transactions from an IC
subnet, with no off-chain relayers. We integrate their SDK. The hard part is theirs.

---

## Skills

**Languages**

![Rust](https://img.shields.io/badge/Rust-000000?style=for-the-badge&logo=rust&logoColor=white)
![Motoko](https://img.shields.io/badge/Motoko-6C4BB6?style=for-the-badge&logo=internetcomputer&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Bash](https://img.shields.io/badge/Bash-4EAA25?style=for-the-badge&logo=gnubash&logoColor=white)

**Internet Computer**

![Internet Computer](https://img.shields.io/badge/Internet%20Computer-29ABE2?style=for-the-badge&logo=internetcomputer&logoColor=white)
![Candid](https://img.shields.io/badge/Candid-4B2E83?style=for-the-badge&logo=internetcomputer&logoColor=white)
![ICRC-1/2](https://img.shields.io/badge/ICRC--1%2F2-0EA5A4?style=for-the-badge&logo=internetcomputer&logoColor=white)
![PocketIC](https://img.shields.io/badge/PocketIC-1F6FEB?style=for-the-badge&logo=internetcomputer&logoColor=white)
![WebAssembly](https://img.shields.io/badge/WebAssembly-654FF0?style=for-the-badge&logo=webassembly&logoColor=white)

Stable memory schema evolution and upgrade safety, inter-canister call and commit-point
discipline, threshold signature and chain-key integrations, Candid interface evolution.

**Governance & anti-abuse design**

Proof of personhood gating, Sybil resistant quadratic voting, liquid democracy and vote
delegation, capture resistant threshold design, in-canister rate limiting, proof-of-work
challenges and cycle-drain defence.

**Frontend**

![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![Tailwind CSS](https://img.shields.io/badge/Tailwind-0B1120?style=for-the-badge&logo=tailwindcss&logoColor=38BDF8)
![Vite](https://img.shields.io/badge/Vite-1B1B1F?style=for-the-badge&logo=vite&logoColor=FFD62E)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)

**Infrastructure & tooling**

![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-1A1A1A?style=for-the-badge&logo=linux&logoColor=FCC624)
![SQLite](https://img.shields.io/badge/SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05033?style=for-the-badge&logo=git&logoColor=white)

**Cross-chain**

![Bitcoin](https://img.shields.io/badge/Bitcoin%20%2F%20ckBTC-F7931A?style=for-the-badge&logo=bitcoin&logoColor=white)
![Solana](https://img.shields.io/badge/Solana%20%2F%20Menese-14F195?style=for-the-badge&logo=solana&logoColor=black)
![Chain-key](https://img.shields.io/badge/Chain--key%20cryptography-29ABE2?style=for-the-badge&logo=internetcomputer&logoColor=white)

---

## This account

One of my GitHub profiles, and the one the OhShii work lives on. The repositories are private,
so what shows up publicly is mostly what I file on other people's projects: bug and security
reports on public Internet Computer repositories.

[My open issues on DFINITY's MULTI/DEX](https://github.com/dfinity/public-multidex/issues?q=author%3Arvnt9999)

---

<div align="center">
<sub>Everything public is linked above.</sub>
</div>
