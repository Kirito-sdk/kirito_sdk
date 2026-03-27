# Kirito SDK
> **Forge Composable, Yield-Enabled NFTs on Stellar – Where Creativity Meets Real-World Finance**

A modular toolkit for creating, minting, and managing programmable NFTs on Stellar using Soroban smart contracts, native asset issuance, and seamless global payments.

Features a powerful **AI-powered Node-Based UI Image Generator** with React Flow and HashLips engine integration.

---
## ✨ Overview

Kirito SDK transforms traditional NFTs into **dynamic, utility-driven financial assets** on the Stellar network.

It combines:
- Stellar’s ultra-low fees, fast finality, and native payments
- Programmable Soroban smart contracts
- **Visual AI image generation** using a node-based editor (React Flow) + HashLips-style generative art engine

This enables creators to build NFTs that are not only visually unique but also financially programmable — perfect for yield-bearing art, memberships, RWAs, and more.

---
## 🚀 Features

### Core NFT Features
* **Programmable NFTs (Soroban)** — Smart NFTs with embedded logic
* **Multi-Asset Rewards** — Yield distribution in USDC or custom tokens
* **Native Payments Integration** — Built-in Stellar payment rails
* **Token Issuance Engine** — Create and manage custom assets
* **Marketplace Support** — Auctions, fixed pricing, royalties
* **Wallet Integration** — Freighter and other Stellar wallets
* **Low Fees + High Speed** — Designed for mass adoption

### AI Image Generator (Node-Based)
* **Visual Node Editor** powered by **React Flow**
* Drag-and-drop nodes for layers, AI prompts, transformations, combiners, and outputs
* **HashLips Art Engine Integration** — Battle-tested layer-based generative art (now with AI enhancements)
* Real-time preview of generated images
* Export metadata-ready assets (images + JSON attributes)
* Support for trait rarity, rarity rules, and custom logic nodes
* Bridge generated art directly into NFT minting workflows

---
## 🏗 Architecture

Kirito SDK is built with modular, composable layers:

1. **AI Image Generation Engine**
   - React Flow node-based UI
   - HashLips core (layer stacking, trait generation, metadata)
   - AI nodes (prompt-based generation, upscaling, style transfer, etc.)

2. **NFT Generation Engine**
   - Trait-based creation with rich metadata

3. **Soroban Contract Layer**
   - Minting, transfers, and programmable logic

4. **Asset Engine**
   - Custom token issuance for rewards/governance

5. **Reward Distribution Manager**
   - Automated yield and royalty payouts

6. **Payment Layer**
   - Fast, cheap Stellar transactions

7. **Marketplace Engine**
   - Listings, bidding, royalty enforcement

8. **Wallet & Storage Layer**
   - Freighter integration + IPFS/Arweave

9. **Interoperability Layer**
   - Cross-chain support

---
## 📦 Installation

```bash
npm install @kirito/stellar-sdk
# or
yarn add @kirito/stellar-sdk
# or
pnpm add @kirito/stellar-sdk
```

For the **AI Image Generator UI** (React component):

```bash
npm install @kirito/stellar-sdk @xyflow/react  # React Flow is now a peer dependency
```

---
## ⚙️ Prerequisites

* Node.js 18+
* Stellar wallet (e.g. Freighter)
* Soroban CLI (optional)
* For UI: React 18+ (or Next.js)

---
## 🚀 Quick Start

### 1. Initialize SDK

```ts
import { createKiritoSDK } from "@kirito/stellar-sdk";

const sdk = createKiritoSDK({
  network: "testnet",
  rpcUrl: "https://soroban-testnet.stellar.org",
});

await sdk.initialize();
```

### 2. Connect Wallet

```ts
const wallet = await sdk.connectWallet();
console.log("Connected:", wallet.address);
```

### 3. Create NFT Collection

```ts
const collection = await sdk.createCollection({
  name: "Kirito Genesis",
  symbol: "KIRITO",
  supply: 1000,
  metadataBaseURI: "ipfs://...",
});
```

### 4. Use the AI Image Generator (Node-Based)

```tsx
import { KiritoImageGenerator } from "@kirito/stellar-sdk/ui";
import { useState } from "react";

function App() {
  const [generatedAssets, setGeneratedAssets] = useState([]);

  return (
    <KiritoImageGenerator
      onGenerateComplete={(assets) => {
        console.log("Generated NFTs ready:", assets);
        setGeneratedAssets(assets); // { image, metadata, traits }
      }}
      hashlipsConfig={{
        // Optional: customize layers, rarity, etc.
        layersOrder: ["background", "body", "eyes", ...],
      }}
      stellarCollectionId={collection.id}
    />
  );
}
```

**Inside the node editor** you can:
- Add **Layer Nodes** (background, clothing, accessories…)
- Connect **AI Prompt Nodes** for generative elements
- Use **Combiners**, **Rarity Filters**, and **Transform Nodes**
- Preview in real-time
- Export directly to IPFS-ready format for minting

### 5. Mint Generated NFTs

```ts
for (const asset of generatedAssets) {
  const nft = await sdk.mintNFT({
    collectionId: collection.id,
    owner: wallet.address,
    metadata: asset.metadata,
    imageURI: asset.image,
  });
}
```

### 6. Distribute Rewards

```ts
await sdk.distributeRewards({
  tokenId: nft.tokenId,
  asset: "USDC",
  amount: "10",
});
```

---
## 💡 Use Cases

* **Creator Monetization** — Yield-paying generative art
* **Membership NFTs** — Visual + utility access tokens
* **Real-World Asset Tokenization** — Beautifully rendered fractional ownership
* **Gaming & Loyalty** — Procedurally generated avatars with on-chain rewards
* **Event Ticketing** — Unique visual tickets with royalties
* **AI Art Collections** — Node-based workflows for complex generative drops

---
## 🔄 Example Workflow

1. Design generative pipeline in **React Flow** node editor
2. Generate thousands of unique images + metadata via HashLips engine
3. Create collection on Stellar
4. Mint NFTs with embedded yield logic
5. Distribute rewards and enable marketplace trading

---
## 🧪 Testing

```bash
npm test
```

---
## 🌐 Networks

* **Stellar Testnet**
* **Stellar Mainnet**

---
## 🔐 Security Best Practices

* Never expose private keys
* Use environment variables for secrets
* Validate all inputs (especially node configurations)
* Audit Soroban contracts before mainnet deployment

---
## 📁 Project Structure

```
kirito-stellar-sdk/
├── src/
│   ├── sdk/              # Core SDK logic
│   ├── contracts/        # Soroban contracts
│   ├── generation/       # NFT & metadata generation
│   ├── image-generator/  # ← New: React Flow + HashLips integration
│   ├── ui/               # React components (KiritoImageGenerator, nodes, etc.)
│   ├── wallet/
│   ├── marketplace/
│   └── utils/
├── tests/
├── examples/
├── docs/
└── README.md
```

---
## 🛠 Development

```bash
# Install dependencies
npm install

# Build project
npm run build

# Run tests
npm test

# Start dev mode (includes UI hot reload)
npm run dev
```

---
## 🤝 Contributing

1. Fork the repo
2. Create a feature branch (`git checkout -b feature/amazing-node`)
3. Add tests for new nodes or engine features
4. Submit a PR

We especially welcome contributions to the **node types**, **AI integrations**, and **HashLips plugin system**.

---
## 📚 Documentation

* API Reference (coming soon)
* [Node-Based Image Generator Guide](./docs/image-generator.md)
* Soroban Contract Guide
* Examples directory

---
## 🗺 Roadmap

* [x] NFT minting engine
* [x] Reward distribution system
* [x] Wallet integration
* [x] **AI Node-Based Image Generator with React Flow + HashLips**
* [ ] Marketplace contracts
* [ ] Advanced AI nodes (Stable Diffusion / Flux integration, etc.)
* [ ] Cross-chain bridges
* [ ] Mobile SDK
* [ ] DAO governance

---
## 🌍 Why Stellar + Visual Generation?

Stellar brings financial infrastructure.  
**React Flow + HashLips** brings intuitive, powerful creative tools.  

Together they make high-quality, yield-enabled NFT creation accessible to artists, developers, and brands worldwide.

---
## 📜 License

MIT License

---
## ❤️ Acknowledgments

* Stellar ecosystem & Soroban team
* HashLips Art Engine (and HashLips Lab)
* React Flow / xyflow team
* Open-source contributors

---
## 🌐 Community

* GitHub: [https://github.com/kirito-sdk](https://github.com/kirito-sdk)
* Discord: (coming soon)
* Twitter: (coming soon)

---

**Made with ❤️ for the Stellar ecosystem + the next generation of visual creators**
```
