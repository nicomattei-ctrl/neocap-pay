# NeoCAP Pay

Simple USDC payment requests built on Arc.

NeoCAP Pay is a lightweight payment prototype for merchants, freelancers and service providers. It lets a user connect a browser wallet, enter a recipient, amount and description, then send native USDC on Arc.

## What it does

1. Discovers browser wallets through EIP-6963.
2. Connects MetaMask (preferred when available).
3. Creates a payment request with recipient, USDC amount and description.
4. Uses Circle App Kit with the viem adapter to estimate and submit the payment.
5. Displays the transaction hash and Arc Explorer URL returned by the payment flow.

## Arc mainnet

The current V1 is configured for Arc mainnet using the App Kit chain identifier `Arc`.

A real mainnet payment was successfully submitted during V1 validation:

- Amount: `0.20 USDC`
- Transaction: `0x375ce13f6715ff5a4594bca63102b64771a1a8fa2ae9abbc91c2bb9ff0918857`
- Explorer: https://explorer.arc.io/tx/0x375ce13f6715ff5a4594bca63102b64771a1a8fa2ae9abbc91c2bb9ff0918857

## Tech stack

- TypeScript
- Vite
- Circle App Kit
- Circle viem adapter
- viem / EIP-1193
- EIP-6963 wallet discovery

## Run locally

```bash
npm install
npm run dev
```

For a production build:

```bash
npm run build
```

The V1 build has been validated successfully with TypeScript and Vite.

## Project structure

```text
index.html
src/
  main.ts       # wallet connection + Arc USDC payment flow
  styles.css    # application UI
package.json
tsconfig.json
```

## Safety

NeoCAP Pay never asks for or stores seed phrases or private keys. Wallet approvals and transaction signing happen in the user's connected wallet.

Always verify the selected network, recipient and amount in the wallet before confirming a mainnet transaction.

## Status

- [x] Browser wallet discovery
- [x] MetaMask connection
- [x] Arc Testnet payment validation
- [x] Arc mainnet configuration
- [x] Real Arc mainnet USDC payment validation
- [x] Production build validation
- [ ] Public production deployment
- [ ] Arc Microgrants submission

## Microgrant

NeoCAP Pay is being prepared as an Arc-native proof of concept for the Arc Microgrants program. The project is intentionally small: the goal is to demonstrate a simple, working USDC payment experience on Arc mainnet before expanding into reusable payment links, QR codes, receipts and merchant tooling.
