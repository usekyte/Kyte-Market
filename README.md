# Kyte Market

The web app and indexer behind [kyte.sh](https://kyte.sh): a non-custodial, fully collateralised options market on
Robinhood Chain. Sell covered calls and cash-secured puts, buy options as transferable NFTs, stake $KYTE.

## What is here

| Folder | What it is |
|---|---|
| `src/` | Next.js 16 app: market, sell, positions, stake, proof, docs |
| `indexer/` | Node service that indexes the contracts' events and serves the app's API (offers, positions, prices, activity) |
| `public/` | Brand assets |
| `contracts/deployments/4663.json` | Addresses the app and indexer read |

Contract sources live in the companion repository. Live addresses: [`CONTRACTS.md`](CONTRACTS.md).

## Run locally

```bash
pnpm install
cp .env.example .env.local      # set NEXT_PUBLIC_PRIVY_APP_ID (your Privy app) and NEXT_PUBLIC_INDEXER_URL
pnpm dev                        # http://localhost:3010
```

Indexer, against Robinhood Chain mainnet:

```bash
CHAIN_ID=4663 RPC_URL=https://rpc.mainnet.chain.robinhood.com node indexer/src/index.mjs   # http://localhost:4200
```

Requires Node 24 and pnpm. The app reads the chain directly when no indexer URL is set, with reduced features.

## Live addresses

| Contract | Address |
|---|---|
| $KYTE token | [`0x072D88c2F31F568C0F4B8F613692eB489541Ed45`](https://robinhoodchain.blockscout.com/address/0x072D88c2F31F568C0F4B8F613692eB489541Ed45) |
| StakingPool | [`0xD7253a90fd43507F44cF0934F3D5d7432760d17f`](https://robinhoodchain.blockscout.com/address/0xD7253a90fd43507F44cF0934F3D5d7432760d17f) |
| BuybackBurner | [`0x8A9d128247D8c4512411CF9D0CdCAc5Acf86FB95`](https://robinhoodchain.blockscout.com/address/0x8A9d128247D8c4512411CF9D0CdCAc5Acf86FB95) |
| FeeVault | [`0x78c569A1137B78cB78F42c42B4B6C2b8F1E3dDef`](https://robinhoodchain.blockscout.com/address/0x78c569A1137B78cB78F42c42B4B6C2b8F1E3dDef) |
| Uniswap v4 swap adapter | [`0xFa17818515E946180b9767f9D9c40A09EE80dda6`](https://robinhoodchain.blockscout.com/address/0xFa17818515E946180b9767f9D9c40A09EE80dda6) |
| KyteHook (Uniswap v4) | [`0x77e52E93Aa0892b29a4527Af4f3a79F01cfa9044`](https://robinhoodchain.blockscout.com/address/0x77e52E93Aa0892b29a4527Af4f3a79F01cfa9044) |
| AssetRegistry (markets v2/v3) | [`0x02f571e10B9c7303EB7A6284A7137b146e18658D`](https://robinhoodchain.blockscout.com/address/0x02f571e10B9c7303EB7A6284A7137b146e18658D) |
| CallMarket (v3) | [`0xb6759D8893601BB7c1A032eC8ea40C856a6adf80`](https://robinhoodchain.blockscout.com/address/0xb6759D8893601BB7c1A032eC8ea40C856a6adf80) |
| PutMarket (v3) | [`0x2E2d5DfB4cf30d15688Cc2DDD30641c78DFfcb35`](https://robinhoodchain.blockscout.com/address/0x2E2d5DfB4cf30d15688Cc2DDD30641c78DFfcb35) |
| Router (v3) | [`0xdD76956667E6423bAC56d2EbF827a9b0d7dBDF68`](https://robinhoodchain.blockscout.com/address/0xdD76956667E6423bAC56d2EbF827a9b0d7dBDF68) |
| OptionNFT (v3) | [`0xE0CD21A7Ed37898A5ACdF7Dc68C52259Cd63308B`](https://robinhoodchain.blockscout.com/address/0xE0CD21A7Ed37898A5ACdF7Dc68C52259Cd63308B) |
| WETH | [`0x0Bd7D308f8E1639FAb988df18A8011f41EAcAD73`](https://robinhoodchain.blockscout.com/address/0x0Bd7D308f8E1639FAb988df18A8011f41EAcAD73) |
| Uniswap v4 PoolManager | [`0x8366a39CC670B4001A1121B8F6A443A643e40951`](https://robinhoodchain.blockscout.com/address/0x8366a39CC670B4001A1121B8F6A443A643e40951) |

## Security

Report vulnerabilities to contact@kyte.sh. Please do not disclose publicly before we have responded.

Options can expire worthless. Nothing here is investment advice. Kyte is built on Robinhood Chain and is not
affiliated with or endorsed by Robinhood.
