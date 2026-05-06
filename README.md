# Conduit Protocol

> Trustless trade finance for the $2.5 trillion global trade gap powered by MUSD on Mezo.

## The Problem

700 million SMBs across emerging markets cannot access letters of credit from their local banks. An importer in Vietnam trying to buy $30,000 of goods from a supplier in Germany faces three options: pay upfront and risk non-delivery, wait 90 days for bank LC approval (which 40% of SMB applications never receive), or simply don't trade.

Traditional letters of credit require correspondent banking relationships, $50K minimums, 8-12 weeks of onboarding, and fees of 1.5-3% per transaction. For SMBs in emerging markets, this system was never built for them.

## The Solution

Conduit replaces the correspondent bank with a smart contract. Using MUSD Mezo's Bitcoin-backed stablecoin as the settlement asset:

1. **Buyer** locks MUSD into a Conduit escrow contract
2. **Seller** receives confirmation of locked funds and ships goods
3. **On delivery confirmation**, MUSD releases automatically to the seller
4. **If delivery fails** by the deadline, MUSD returns to the buyer automatically
5. **Disputes** are resolved via a designated arbitrator (multi-sig pattern)

No correspondent banks. No minimums. No 12-week onboarding. Trustless trade finance, settled in Bitcoin-backed dollars.

## Why MUSD

MUSD is the ideal settlement asset for cross-border trade finance:
- **Stable**: 1:1 USD peg, eliminating FX risk during the trade cycle
- **Bitcoin-backed**: 100% collateralized by BTC no counterparty risk
- **Permissionless**: any buyer or seller with a wallet can participate
- **Fixed cost**: 1% APR borrowing means buyers can mint MUSD cheaply against BTC holdings

## Architecture

### Smart Contracts (Solidity, Mezo EVM)
- `ConduitEscrow.sol` core escrow logic: lock, release, refund, dispute
- `ConduitFactory.sol` creates individual LC instances per trade
- `ConduitArbitrator.sol` multi-sig dispute resolution

### Frontend
- React + ethers.js
- Mezo Passport wallet connection
- Buyer dashboard: create LC, fund, track status
- Seller dashboard: view incoming LCs, confirm shipment
- Arbitrator panel: review and resolve disputes

### Mezo Testnet
- RPC: https://rpc.test.mezo.org
- Chain ID: 31611
- MUSD contract integrated for escrow funding

## Target Users

| Role | Location | Pain Point |
|---|---|---|
| SMB Importer | Vietnam, Kenya, Colombia, Morocco | Cannot get bank LC |
| SMB Exporter | China, Germany, UAE | Ships goods with no payment guarantee |
| Freight Forwarder | Global | Manual document verification |

## Market

- $2.5 trillion global trade finance gap (WTO/ADB)
- 40% of SMB LC applications rejected in developing economies
- $5 trillion annual trade finance market
- 0 trustless on-chain LC products exist today

## Track

**MUSD Track** Supernormal dApps (Mezo Hackathon 2026)

## Status

Mid-hackathon checkpoint: Architecture defined, smart contract development in progress on Mezo testnet.

## Team

- Aqeelerh: Product, Research, Market Strategy

## Built With

- Solidity
- Hardhat
- React
- ethers.js
- Mezo EVM (testnet)
- MUSD (Mezo Bitcoin-backed stablecoin)
