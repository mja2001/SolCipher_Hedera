
# 🔒 SolCipher: Secure Document Sharing on Hedera

A **privacy-first Decentralized Application (dApp)** for **secure document sharing** built on the **Hedera network**. It combines client-side encryption with on-chain access control to create a secure, auditable, and accessible file-sharing platform.

## ✨ Features

  * **Client-Side Encryption:** Uses **AES-256-GCM** to encrypt all file contents in the user's browser before upload.
  * **Decentralized Storage:** Encrypted files are stored on **IPFS**, and the resulting Content Identifier (CID) is securely anchored to the Hedera network.
  * **Smart Contract Access Control:** A **Solidity smart contract** on Hedera manages file ownership, recipient permissions, and access revocation.
  * **Immutable Logging:** File share events (including unique file ID and expiry) are logged to the **Hedera Consensus Service (HCS)** for an immutable audit trail.
  * **File Revocation:** The sender can **revoke** a file at any time, instantly invalidating the recipient's ability to view it via the smart contract.

## 🛠️ Tech Stack

| Component | Technology | Description |
| :--- | :--- | :--- |
| **Blockchain** | Hedera (HFS, HCS, Smart Contracts) | Ledger for CIDs, access control, and logging. |
| **Frontend** | Next.js, React, CSS Modules | Client-side application for file encryption and sharing UI. |
| **Smart Contracts** | Solidity (`SolCipherHedera.sol`), Hardhat | Contract for managing file access and revocation logic. |
| **Storage** | IPFS, Web3.Storage | Decentralized storage for the encrypted file payload. |
| **SDKs/Libs** | `@hashgraph/sdk`, `ethers` | Tools for interacting with the Hedera network and smart contracts. |

-----

## 🚀 Getting Started

To get the SolCipher dApp running locally, follow these steps.

### Prerequisites

You must have the following installed:

  * Node.js (LTS version recommended)
  * npm or yarn
  * Git

### Installation and Setup

1.  **Initialize the Repository**:

    ```bash
    mkdir SolCipher
    cd SolCipher
    git init
    ```

2.  **Create Directory Structure**:

    ```bash
    mkdir -p client/{components,pages,utils,styles,public/images}
    mkdir -p programs/solcipher-hedera/{contracts,scripts,test}
    mkdir scripts tests
    ```

3.  **Install Dependencies**:

    ```bash
    # Install client (frontend) dependencies
    cd client
    npm install --save @hashgraph/sdk ethers web3.storage next react react-dom
    npm install --save-dev @testing-library/react @testing-library/jest-dom jest

    # Install program (smart contract/backend) dependencies
    cd ../programs/solcipher-hedera
    npm init -y
    npm install --save-dev @nomiclabs/hardhat-ethers ethers dotenv hardhat
    ```

4.  **Configure Environment**:

    ```bash
    cd ../..
    cp .env.example .env
    chmod +x scripts/setup-env.sh scripts/deploy-hedera.sh
    ./scripts/setup-env.sh
    ```

    > **Note:** You must manually update the newly created `.env` file with your **Hedera Account ID**, **Private Key**, and **Web3.Storage Token**.

5.  **Deploy Contracts** (If applicable):

      * *The documentation does not provide the final deployment command, but a script is present:* `scripts/deploy-hedera.sh`. Use the appropriate Hardhat command to run this script.

6.  **Run the dApp:**

    ```bash
    cd client
    npm run dev
    ```

-----

## 💡 How It Works

The core sharing process is handled by `FileShare.js` and the `SolCipherHedera.sol` contract.

1.  **User Selects File:** The file is selected in the client-side UI.
2.  **Encryption:** `encryptFile` utility generates a random key and encrypts the file with **AES-256-GCM**.
3.  **Storage:** The encrypted file is uploaded to **IPFS**, returning a unique **CID**.
4.  **On-Chain Record:** The **CID** is stored in the **Hedera File Service**.
5.  **Access Control:** The `shareFile` function on the `SolCipherHedera.sol` contract is called with the CID, recipient address, and expiry time, setting up the access rules.
6.  **Logging:** A record of the share is submitted to a **Hedera Consensus Service (HCS)** topic for an immutable history.
