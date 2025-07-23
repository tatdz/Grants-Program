# Milkyway2

- **Team Name:** Milkyway2  
- Payment address: 121v9xMyaesfMXML47xYP4PvqW6GQUFjjuZXxw9RBnGpmaeG  
- **Level:** 1

## Project Overview :page_facing_up:

### Overview

**Milkyway2** is a decentralized risk classification and incident reporting application for validators in the Polkadot, Kusama, and parachain ecosystems. It incorporates zero-knowledge cryptographic primitives, a privacy-focused design, encrypted validator messaging, and real-time validator monitoring to improve network security and transparency.

The application classifies validators using a traffic-light-style risk system (RED / YELLOW / GREEN), enables **anonymous zk reporting**, supports **encrypted validator messaging using Ed25519 + AES-256**, and visualizes **OpenGov governance activity** within an intuitive frontend dashboard. Milkyway2 is powered by the **Semaphore protocol** for Sybil resistance and is designed for multi-wallet compatibility and cross-chain use.

The project won the **Polkadot track at the Web3 Foundation Summit Hackathon in Berlin (July 2025)**.

---

### Project Details

#### Mockups/designs of any UI components

The frontend and UI designs, with well-structured components that include:

- A homepage with validator status and live event feeds  
- `Validator` exploration dashboard showing rankings and suggestions  
- `Report Validator` page with zk form flow  
- `Governance` tracker with OpenGov proposal visualizations  
- `Validator Messaging` portal for encrypted key generation and message viewing  
- `Multi-Wallet` interface via SubWallet and Polkadot.js integration  
- `Analytics Export` interface for dataset download (in progress)

> _Design prototypes and implementation live in `/client/pages`, `/hooks`, and `/components` folders._

---

#### Data Models / API Specifications

Milkyway2 includes a backend built with **Node.js (Express)** and **TypeScript**, exposing the following RESTful endpoints:

| Endpoint                    | Functionality                                                      |
|-----------------------------|---------------------------------------------------------------------|
| `POST /submitProof`         | Submit zero-knowledge anonymous incident report                    |
| `GET /validator/:id/stats`  | Retrieve validator’s current reputation and traffic-light status    |
| `POST /messages/send`       | Send an AES+Ed25519-encrypted message to validator group           |
| `GET /governance/trending`  | Provide referenda details and voting analytics                     |
| `GET /export`               | Export CSV/JSON dataset of risk history or reports (in progress)    |

APIs are served via the `server/routes.ts` file with shared types and schema validation via `shared/schema.ts`.

---

#### Technology Stack

**Frontend:**

- React 18 + TypeScript  
- TailwindCSS + shadcn/ui for UI components  
- TanStack React Query for state coordination  
- Wouter for routing  
- Vite for dev & build optimization  

**Backend:**

- Node.js + Express for API logic (RESTful)
- Drizzle ORM for type-safe querying  
- PostgreSQL (with planned migration to production persistence)  
- TypeScript throughout backend

**Blockchain/zk Integration:**

- `@polkadot/api`, `@polkadot/extension-dapp` for blockchain connectivity  
- `@semaphore-protocol` for identity registration and proof generation  
- **Group encrypted messaging**: AES-256 + Ed25519  
- **Smart Contracts**:
  - `zkAttestation` (Semaphore)  
  - `EncryptedGroupMessages` (message layer storage - Passet testnet)

**Security:**

- Client-verified proof generation  
- Identity nullifier to prevent proof double-spending  
- Persistent sessions (localStorage) for wallet sessions  
- In-memory fallback storage for dev (Postgres prod-ready support)

---

#### Documentation

- **Architecture Overview** – includes backend stack, validator lifecycle, ZK integration, and Passet layer  
- **Contributor Guide** – covers environment setup and dev practices  
- **REST API Specification** – documented in `routes.ts` and validated with shared types  
- **Message Signing/Encryption Flow** – documented with UI examples and cryptographic boundaries

_You’ll find these in the `/shared`, `/server`, and `/client/docs` folders._

---

#### Proof-of-Concept / MVP Achievements

- Live React dashboard running validator risk classification  
- Real-time risk system (RED, YELLOW, GREEN) based on uptime, commission, slash history  
- Semaphore-based zero-knowledge report form integrated and generating on-device proofs  
- Basic encrypted validator messaging (AES+Ed keys) being sent to smart contract  
- Multi-wallet session handling (SubWallet, Polkadot.js) tested  
- Internal Westend testnet deployed to simulate uptime drops and active voting data feeds

---

#### What this project is *not*:

- ❌ No on-chain runtime or parachain development  
- ❌ No tokenomics, slashing extrinsics, or reward mechanisms  
- ❌ Not a redundant telemetry copy (focus is **incident responses** + zk privacy)  
- ❌ Does not expose validator inbox addresses or proof identities

---

## Ecosystem Fit

### Where and how does it fit?

Milkyway2 enables decentralized community oversight of validators using anonymous proofs, governance analytics, and encrypted communications—all features **currently missing** from Polkadot telemetry and on-chain modules.

It strengthens the accountability of the active set by enabling incident reports and tracking performance metrics across chains.

### Target Audience

- Validator operators (incident reporting, encrypted messaging)  
- Nominators (choosing safe, well-behaved validators)  
- On-chain governance participants  
- Observability tools / explorers (data export & analytics feed consumers)  

### Needs Addressed

- Privacy-preserving validator whistleblowing  
- Analytics derived from incident signals, not just uptime    
- Cross-chain validator status comparison with governance correlation  
- Community feedback loops without reputation attacks or doxing

### Validation

- ✅ Governance discussions around validator identity, malicious behavior (e.g. OpenGov referenda)  
- ✅ Polkadot validator/operator chats (ChaosDAO, Polkachu) calling for accountability tooling  
- ✅ First-hand experience operating validators in Cosmos and Chainlink  
- ✅ Judging panel endorsement at **Web3 Summit Hackathon (2025 winner - Polkadot track)**

---

## Team :busts_in_silhouette:

### Team Members

- **Product:** Tatiana Dzhambinova  
- **Developer:** Pavel Shibaev  

### Contact

- **Contact Name:** Tatiana Dzhambinova  
- **Contact Email:** [tatiana.dzhambinova@gmail.com](mailto:tatiana.dzhambinova@gmail.com)

### Team Experience

**Tatiana Dzhambinova**  
- Product development across blockchain, AI, and fintech platforms  
- Founded a startup in KYB / reusable business IDs  
- Led product delivery for governance and cross-chain tooling platforms

**Pavel Shibaev**  
- Designed RPC polling services for 20+ Cosmos chains  
- Managed 40+ active servers across 50+ chains  
- Built full Chainlink Oracle stack manifests (Kubernetes-based)  
- Maintained mission-critical blockchain infra in production

### Code Repos

- https://github.com/tatdz/milkyway2

### GitHub Profiles

- https://github.com/tatdz  
- https://github.com/shibaeff  

---

## Development Status :open_book:

- Won Polkadot track at Web3 Summit Hackathon (Berlin, July 2025)  
- Active frontend + backend MVP live on localhost  
- ZK proofs generating in-browser, integrated with UI  
- Governance dashboard and validator risk logic in use (RED/YELLOW/GREEN)  
- Smart contract storage (EncryptedGroupMessages) deployed on Passet  
- CLI functionality planned for validators

---

## Roadmap :nut_and_bolt:

### Overview

- **Total Duration:** 3 months  
- **FTE:** 1 (split across 2 part-time contributors)  
- **Total Cost:** $10,000  
- **DOT %:** 70%

---

### Milestone 1 — Mainnet Launch & Feature Freeze
**1 month | 2 FTE | 3,500 USD**

| No. | Deliverable              | Specification |
|-----|--------------------------|---------------|
| 0a  | License                  | MIT License across all repositories |
| 0b  | Documentation            | Final schema and proof lifecycle docs |
| 0c  | Testing Guide            | Tests for risk tiering and zk-proof flows |
| 0d  | Docker                   | Compose file supporting Node API, PostgreSQL, client |
| 1   | Mainnet Integration      | Dashboard connected to Kusama + Passet mainnets |
| 2   | Semaphore Proof Module   | Finalized client interface for proof lifecycle |
| 3   | Offline Incident Logging | Append-only event journal for slashing/offline validators |
| 4   | Validator CLI            | Generate/export/report commands for operators |

---

### Milestone 2 — Advanced Analytics & Export
**1 month | 2 FTE | 3,500 USD**

| No. | Deliverable            | Specification |
|-----|------------------------|---------------|
| 0a  | License                | MIT |
| 0b  | Docs                   | Export feature usage guides |
| 0c  | Export Testing Suite   | Schema mappings for JSON/CSV download formats |
| 1   | Export API             | Download validator performance + incident JSON/CSV |
| 2   | Multi-Wallet Support   | Session persistence and wallet-switching logic |
| 3   | Trend Graphs           | Uptime and slash analytics (line/bar charts) |
| 4   | Governance Evaluation  | Metric overlays for validator voting record analytics |

---

### Milestone 3 — Validator Partnership Test & Calibration
**1 month | 2 FTE | 3,000 USD**

| No. | Deliverable               | Specification |
|-----|---------------------------|---------------|
| 0a  | License                   | MIT |
| 0b  | Partnership Report        | Feedback docs from test validators |
| 0c  | Testnet Replay Harness    | Recreated downtime/slash events in staging |
| 0d  | Message Flow UX Tests     | Validator ↔ user reporting flow test coverage |
| 0e  | Public Article            | Milestone summary + zkValidatorOps pilot writeup |
| 1   | Partnership MoUs          | at least 1 validator MoU (via W3F network) signed |
| 2   | Risk Score Calibration    | Adjust thresholds based on validator results |
| 3   | Explorer Feed Integration | Export dataset format for third-party tools like Subscan |

---

## Future Plans

- Expand multi-chain scope to include parachains and testnets (e.g., Collectives, Rococo)  
- Add on-chain fallback attesters for sealed anonymous vote exports  
- Collaborate with ecosystem data providers / dashboards / more validators/ DeFi  
  
---

## Referral Program

- **Referrer:** N/a  


