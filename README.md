# PayQuick

PayQuick is a stablecoin payment application built on **Arc** that enables small merchants and businesses to accept fast USDC payments through wallet transfers and QR code payment requests.

**Live demo:** https://pay-quick-lime.vercel.app/
**Also deployed on GitHub Pages:** https://naseer32.github.io/PayQuick/

---

## Problem

Small businesses often struggle to accept digital payments that are fast, inexpensive, and easy to use across borders. Traditional crypto payments are also awkward for everyday use — the payer needs to already know the merchant's exact wallet address and the right amount, which is error-prone and unfriendly for a non-technical customer.

## Solution

PayQuick uses Arc's stablecoin-native infrastructure to make requesting and receiving USDC payments simple. A merchant generates a payment request — amount, currency, and what it's for — and shares it as a link or QR code. The customer just opens it and taps "Pay." No manually copying wallet addresses, no typing in amounts, and every USDC payment is recorded in a transparent on-chain history.

## Features

- **Connect Wallet** — connects to MetaMask, auto-configures Arc Testnet if needed
- **Send** — send USDC or EURC directly to any wallet address, with an optional memo
- **Request Payments** — generate a shareable payment request for a specific amount and currency
- **QR Code Payments** — every request also renders as a scannable QR code
- **Payment History** — a transparent, on-chain ledger of every USDC payment sent or received
- **Built on Arc Testnet**

## Why Arc?

- USDC as the native gas token — predictable, dollar-denominated fees
- Fast, deterministic finality
- Full EVM compatibility — standard tooling (ethers.js, MetaMask) works out of the box
- Stable transaction fees, well suited for everyday merchant payments

## Tech Stack

- HTML / JavaScript (single-file frontend, no backend required)
- ethers.js
- Arc Testnet

## How it works technically

The entire app is a single static HTML file — no backend, no database. A payment request is encoded directly into a URL as query parameters (recipient, amount, currency, memo). When that link is opened, the page detects the parameters and renders a "pay this request" view instead of the normal app. USDC payments go through a custom `PaymentTracker` smart contract's `sendPayment` function, so they're automatically recorded in the shared on-chain history. EURC — Circle's euro stablecoin — is supported as a second currency via the standard ERC-20 `transfer` interface.

## Smart contract

- **PaymentTracker**: `0xd0c5f3e9570CcA0E9913522905b164304A692166` (Arc Testnet)
- **EURC**: `0x89B50855Aa3bE2F677cD6303Cec089B5F319D72a` (Arc Testnet)
- [View on Arc Testnet Explorer](https://testnet.arcscan.app/address/0xd0c5f3e9570CcA0E9913522905b164304A692166)

## Try it

1. Open the [live demo](https://pay-quick-lime.vercel.app/) in a browser with MetaMask (or open it inside MetaMask's built-in browser on mobile).
2. Connect your wallet — PayQuick will prompt you to add Arc Testnet automatically if you don't have it yet.
3. Get free testnet USDC or EURC from [faucet.circle.com](https://faucet.circle.com).
4. Try sending a payment, or create a request and open the link yourself to see the pay flow.

## Roadmap

- Merchant dashboard
- Payment receipts
- Invoice generation
- Payment links
- Analytics
- Unified payment history across USDC and EURC

---

Built for the **Arc Hackathon** (Encode Club, Programmable Money on Arc).
