# Aegis AI v2: Decentralized AI Trust, Provenance, & Escrow Platform on Cardano

Aegis AI v2 is a decentralized, privacy-first AI marketplace and model registry built on the **Cardano Preprod Testnet**. It bridges the gap between healthcare data providers, AI researchers, and commercial entities by offering verifiable dataset provenance, cryptographic escrow payments, and secure model execution checkers.

---

## 🚀 Key Features

### 1. AI Data Provenance Graph (9-Node Lineage)
Tracks the complete lifecycle of a dataset, cryptographically verifying each transition on-chain:
* **Hospital (Provider)** ➔ **Dataset v1** ➔ **Dataset Certificate NFT** ➔ **License NFT** ➔ **Training Job** ➔ **AI Model** ➔ **Research Paper** ➔ **Commercial Product** ➔ **Royalties**
* Built with an interactive SVG visualization that pulls live audit records directly from Cardano metadata.

### 2. Multi-Metric Trust Engine
Datasets are evaluated side-by-side on three critical axes:
* **Dataset Trust Score**: Computes completeness, bias ratios, and structural integrity.
* **AI Readiness Index**: Analyzes feature formats, null values, and machine-learning compatibility.
* **Compliance Index**: Verifies regulatory standards like HIPAA (for medical data) or GDPR.

### 3. Secure AI Workspace
A sandboxed VM dashboard that simulates Jupyter Notebook training workflows:
* Mounts licensed datasets directly into secure containers.
* Monitors hardware parameters (GPU Temp, CPU Load, VRAM) in real-time.
* Allows developers to **"Export Model Weights"** to record checkpoint hashes on the Cardano ledger, minting checkpoint certification NFTs.

### 4. Smart Contract Escrow & License NFTs
Automates licensing agreements using Cardano smart contracts:
* Integrates **Lucid Evolution** client-side library to lock dataset metadata/datum in a smart contract.
* On purchase, routes **95% of payment to the dataset creator** and a **5% treasury split** to the platform pool.
* Instantly mints a **CIP-25 compliant License NFT** directly into the buyer's wallet (e.g., Lace, Nami, Eternl).

### 5. Verified AI Model Registry
A structured database linking trained models directly back to their source training datasets:
* Catalogs models by **ML Framework** (PyTorch, TensorFlow, Scikit-Learn) and **Inference Task** (Classification, Segmentation, Detection, etc.).
* Enables audits to verify that models were trained on properly licensed, certified datasets.

### 6. ADA-Weighted Governance
Allows the community to vote on dataset verification rules and direct platform treasury allocations using connected wallets.

---

## 🛠️ Technology Stack
* **Frontend**: Next.js 15, CSS (Premium Neon & Neon Glassmorphism theme)
* **Blockchain Integration**: Lucid Evolution, WebAssembly, Blockfrost API
* **Smart Contracts**: Aiken (Validator located in `contracts/validators/marketplace.ak`)
* **Decentralized Storage**: Pinata IPFS (used for live metadata and dataset pinning)
* **Wallet Compatibility**: Lace, Nami, Eternl (CIP-30 standard)

---

## 📁 Repository Structure
```
Aegis_AI/
├── components/          # Reusable UI Components (Provenance Graph, Compare Modals)
├── contracts/           # Aiken Smart Contract validators & compiler configs
│   ├── validators/      # Validator files (marketplace.ak)
│   └── aiken.toml       # Aiken project specifications
├── lib/                 # Cardano blockchain & Lucid utility functions
├── pages/               # Next.js router pages (Marketplace, Dashboard, Models, Governance)
├── styles/              # Global animations and neon glassmorphism CSS
├── env.example          # Environment configuration specs
└── README.md            # Project description & setup documentation
```

---

## ⚙️ Local Development Setup

1. **Clone the repository**:
   ```bash
   git clone <repo_url>
   cd Aegis_AI
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Configure Environment Variables**:
   Create a `.env.local` file in the root of the team directory and copy the contents of `env.example`:
   ```env
   # Cardano Blockchain Configuration
   NEXT_PUBLIC_BLOCKFROST_PROJECT_ID=your_blockfrost_preprod_project_id
   NEXT_PUBLIC_CARDANO_NETWORK=Preprod
   NEXT_PUBLIC_SCRIPT_ADDRESS=your_plutus_escrow_address
   NEXT_PUBLIC_SCRIPT_HASH=your_plutus_escrow_hash

   # Pinata IPFS Storage Configuration
   NEXT_PUBLIC_PINATA_API_KEY=your_pinata_api_key
   NEXT_PUBLIC_PINATA_API_SECRET=your_pinata_api_secret
   NEXT_PUBLIC_PINATA_JWT=your_pinata_jwt_token
   ```

4. **Run the local development server**:
   ```bash
   npm run dev
   ```
   Open [http://localhost:3000](http://localhost:3000) in your browser.

---

## 💡 How to Test & Demo the Platform
1. **Connect Wallet**: Click the "Connect Wallet" button. You can connect a real **Lace** or **Nami** wallet loaded with Preprod ADA, or select **Simulation Mode** to instantly explore with a simulated balance.
2. **Register a Dataset**: Go to `/upload`, upload a file, and click **Secure Audit**. With your Pinata key configured, the file will perform live IPFS pinning.
3. **Purchase License**: Go to the Marketplace, view the side-by-side dataset compare modal, open a dataset passport, and purchase a license to mint the License NFT.
4. **Train Model**: Go to your Dashboard, open the Secure AI Workspace, select the licensed dataset, run the training job, and click **Export Model Weights** to mint a checkpoint NFT.
5. **Model Registry**: Go to `/models` and register your PyTorch/TensorFlow models with clear task tags.
