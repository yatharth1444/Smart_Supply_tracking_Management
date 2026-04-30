# Supply Chain Blockchain DApp

<div align="center">

![Supply Chain Blockchain]

**A decentralized supply chain management system built on Ethereum blockchain using Solidity smart contracts, Next.js, and Web3.js**

</div>

## Overview

**Supply Chain Blockchain DApp** is an open-source, blockchain-based supply chain management application built with Solidity smart contracts, Hardhat, Next.js, Web3.js, and MetaMask. It demonstrates how to build an end-to-end Ethereum decentralized application (dApp) for transparent, secure, and traceable pharmaceutical supply chains.


### Key Benefits

- **Transparency**: All transactions and product movements are recorded on the blockchain
- **Security**: Immutable records prevent tampering and fraud
- **Efficiency**: Automated processes reduce administrative overhead
- **Traceability**: Complete product journey from raw materials to consumer
- **Decentralization**: No single point of failure

## Features

- **Role-Based Access Control**: Secure role assignment (Owner, Raw Material Supplier, Manufacturer, Distributor, Retailer)
- **Product Management**: Add and track products through the entire supply chain
- **Supply Chain Flow**: Manage product stages (Order → Raw Material Supply → Manufacturing → Distribution → Retail → Sold)
- **Real-Time Tracking**: Track products with detailed stage information and QR codes
- **Modern UI**: Responsive interface built with Next.js and Tailwind CSS
- **Web3 Integration**: Seamless connection with MetaMask wallet
- **Mobile Responsive**: Works well on desktop and mobile devices

## Technology Stack

### Frontend
- **Next.js 14** - React framework with App Router
- **TypeScript** - Type-safe development
- **Tailwind CSS** - Utility-first CSS framework
- **Web3.js** - Ethereum blockchain interaction
- **QRCode.react** - QR code generation for product tracking

### Backend/Blockchain
- **Solidity ^0.8.19** - Smart contract programming language
- **Hardhat** - Ethereum development environment
- **Ganache** - Personal blockchain for development
- **MetaMask** - Web3 wallet integration

### Development Tools
- **Node.js 18+** - JavaScript runtime
- **npm/yarn** - Package management
- **Git** - Version control

## Architecture


The application follows a decentralized architecture where:

1. **Smart Contracts** (Solidity) handle all business logic and data storage on the blockchain
2. **Frontend** (Next.js) provides the user interface and interacts with the blockchain via Web3.js
3. **MetaMask** acts as the bridge between users and the Ethereum network
4. **Ganache** provides a local blockchain for development and testing

### System Flow

```
User → Next.js Frontend → Web3.js → MetaMask → Ethereum Network → Smart Contract
```



### Supply Chain Flow

The product journey through the supply chain:

```
Order → Raw Material Supplier → Manufacturer → Distributor → Retailer → Consumer
```

## Installation

### Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (v18 or higher) - [Download](https://nodejs.org/)
- **Git** - [Download](https://git-scm.com/downloads)
- **Ganache** - [Download](https://trufflesuite.com/ganache/)
- **MetaMask** - [Chrome Extension](https://chrome.google.com/webstore/detail/metamask) | [Firefox Add-on](https://addons.mozilla.org/en-US/firefox/addon/ether-metamask/)
- **VS Code** (Recommended) - [Download](https://code.visualstudio.com/)

### Step 1: Clone the Repository

```bash
git clone https://github.com/yatharth1444/Smart_Supply_tracking_Management
cd Smart_Supply_tracking_Management
```

### Step 2: Install Dependencies

Install root dependencies (for Hardhat):

```bash
cd backend
npm install
cd ..
```

Install client dependencies:

```bash
cd client
npm install
cd ..
```

### Step 3: Configure Ganache

Follow the detailed walkthrough: **[Setting up Ganache (step by step)](#setting-up-ganache-step-by-step)**. In short, use **RPC** `http://127.0.0.1:7545` and **chain ID** **1337** so they match `backend/hardhat.config.ts` (`networks.ganache`) and the keys in `client/src/deployments.json`.

## Setting up Ganache (step by step)

This project’s default Hardhat network `ganache` uses **`http://127.0.0.1:7545`** and **chain ID `1337`**. MetaMask, Ganache, and Hardhat must all use the **same** RPC URL and **chain ID** (EIP-155), or you will see “wrong network” or “contract not found”.

**2. Add the network in MetaMask**  
Network menu → **Add network** → **Add a network manually**, then set:

- **Network name:** e.g. `Ganache Local`
- **RPC URL:** same as Ganache (e.g. `http://127.0.0.1:7545`)
- **Chain ID:** `1337` (must match Ganache and Hardhat `networks.ganache`)
- **Currency symbol:** `ETH`

## Usage Guide

### 1. Register Roles

- Navigate to "Register Roles" page
- Only the contract owner can register new roles
- Add participants: Raw Material Suppliers, Manufacturers, Distributors, and Retailers
- Each role requires: Ethereum address, name, and location

### 2. Order Materials

- Go to "Order Materials" page
- Only the contract owner can create orders
- Enter product details: ID, name, and description
- Ensure at least one participant of each role is registered

### 3. Manage Supply Chain Flow

- Access "Supply Chain Flow" page
- Each role can perform their specific action:
  - **Raw Material Supplier**: Supply raw materials
  - **Manufacturer**: Manufacture products
  - **Distributor**: Distribute products
  - **Retailer**: Retail and mark as sold

### 4. Track Products

- Visit "Track Materials" page
- Enter a product ID to view its complete journey
- View detailed information about each stage
- Generate QR codes for product verification

## Smart Contract Details

The `SupplyChain.sol` smart contract implements a supply chain for the **pharmaceutical** domain: it tracks medicine **stages**, stores names, descriptions, and current stage, and defines **roles** (raw material supplier, manufacturer, distributor, retailer). The **owner** registers participants and creates orders; other functions advance the product and **read** stage and history.


### Roles

- **Owner**: Deploys the contract and can register other roles
- **Raw Material Supplier (RMS)**: Supplies raw materials
- **Manufacturer (MAN)**: Manufactures products
- **Distributor (DIS)**: Distributes products
- **Retailer (RET)**: Sells products to consumers

### Product Stages

1. **Ordered** (Stage 0): Product order created
2. **Raw Material Supplied** (Stage 1): Raw materials supplied
3. **Manufacturing** (Stage 2): Product being manufactured
4. **Distribution** (Stage 3): Product in distribution
5. **Retail** (Stage 4): Product at retailer
6. **Sold** (Stage 5): Product sold to consumer

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request
