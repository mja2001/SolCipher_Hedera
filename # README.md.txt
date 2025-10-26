# README.md
# SolCipher: Secure Document Sharing on Hedera

[cite_start]SolCipher is a privacy-first decentralized application (dApp) for secure document sharing on the Hedera network[cite: 1223, 1814].

[cite_start]It utilizes the following technologies for a secure and decentralized architecture[cite: 1224, 1815]:
* **Client-side AES-256-GCM encryption** for data privacy.
* **Hedera File Service and IPFS** for decentralized file storage.
* **Solidity smart contracts** for access control and permissioning.
* **Hedera Consensus Service (HCS)** for immutable logging of file share events.

## Project Structure

The project contains a Next.js frontend (`/client`) and a Hardhat development environment for the smart contracts (`/programs/solcipher-hedera`).

## Setup Instructions

Please refer to the `setup-env.sh` and `deploy-hedera.sh` scripts in the `scripts/` directory for automated setup after copying all file contents.