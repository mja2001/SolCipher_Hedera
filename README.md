# SolCipher on Hedera – Secure Document Sharing

Privacy-first dApp for encrypted document sharing between Hedera wallets. Integrates client-side encryption, IPFS storage, and on-chain access control via Hedera Hashgraph.

## Why SolCipher on Hedera?
- **End-to-End Encryption**: AES-256-GCM in browser.
- **Decentralized Storage**: IPFS via Web3.Storage.
- **On-Chain Control**: Hedera smart contracts for permissions/expiries.
- **Wallet Integration**: HashPack/Blade for seamless sharing.
- **Batch & Auto-Expiry**: Efficient multi-file uploads with revocation.

## Architecture
```
User → Encrypt (AES-256-GCM) → IPFS Upload → Hedera Contract Record → Recipient Decrypts
```

## Project Description
SolCipher is a groundbreaking privacy-first decentralized application (dApp) built on the Hedera Hashgraph network, designed to revolutionize secure document sharing in the Web3 era. Imagine a world where you can share sensitive files—like legal contracts, medical records, or financial statements—with complete confidence, knowing they're protected by end-to-end encryption and decentralized controls that no central authority can tamper with.

At its core, SolCipher addresses the critical challenges of data breaches and unauthorized access in traditional centralized platforms. Users encrypt files client-side using robust AES-256-GCM encryption before uploading them to IPFS for immutable, decentralized storage. Access permissions, expirations, and revocations are managed on-chain via Solidity smart contracts deployed on Hedera, ensuring transparency and auditability. We integrate Hedera's powerful services: the File Service for storing hashes and metadata, the Consensus Service for tamper-proof logging of events, and optional Token Service for tokenized access—all powered by low-cost HBAR transactions.

Key features include batch uploads, auto-expiry timers to automatically revoke access after a set period, and seamless wallet integration with tools like HashPack or Blade. This makes it ideal for professionals in healthcare, finance, and legal sectors who need compliance, privacy, and efficiency without the risks of single-point failures seen in tools like Dropbox or DocuSign.

What sets SolCipher apart in the Hedera ecosystem? It's faster and cheaper than Ethereum-based alternatives, thanks to Hedera's high-throughput DAG consensus, and it's eco-friendly with a carbon-negative footprint. Our frontend is built with Next.js and React for a user-friendly experience, while the backend leverages Ethers.js and the Hedera SDK for secure operations.

In this hackathon, we're showcasing not just innovation but resilience: A recent pentest report by cybersecurity expert Wessam Al-Khushman validates our architecture against OWASP Web3 Top 10 threats, highlighting strong cryptographic practices and vulnerability mitigations. Looking ahead, we plan mainnet deployment, beta testing, feature expansions like multi-recipient sharing, and pursuing Hedera grants to scale.

## Resources
- **Pentest Certification Report**: [View Report](https://drive.google.com/file/d/1FGb7xPXva32vTgYjCCIiNubsH8jTFWsK/view)
- **Hackathon Presentation**: [View Presentation](https://docs.google.com/presentation/d/1CNKVFEhwk7ooPx9kprNUOg6kJoIYN7H-/edit?slide=id.p1#slide=id.p1)

## Installation
1. Clone: `git clone https://github.com/your-username/solcipher-hedera.git`
2. Install root deps: `yarn install` (if monorepo)
3. Contracts: `cd contracts && npx hardhat compile`
4. Client: `cd client && npm install`
5. Set .env (Hedera testnet ID, key, etc.)

## Usage
- Deploy contracts: `./scripts/deploy-testnet.sh`
- Run frontend: `cd client && npm run dev`
- Connect wallet, upload/share files.

## Contributing
Fork, PRs welcome!

## License
MIT
