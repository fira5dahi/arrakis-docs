# HOT AMM Overview

LPs are getting rekt by toxic order flow. HOT improves returns and maximizes capital efficiency for LPs, by internalizing MEV using an intent-based design.

To learn more, refer to this [HOT AMM: Concepts](../../modules/hotAmm/concepts.md) page.

Just want to deposit? Here's our [New User Interface](https://app.arrakis.finance/modular)

HOT was designed by Arrakis and Valantis Labs. It is built on the [Valantis Modular DEX Framework](https://docs.valantis.xyz/). HOT is the first integration on Arrakis Modular and is powered by Arrakis's offchain market making infrastructure.

### Flagship Public Vault using HOT AMM

Our flagship WETH/USDC Arrakis Modular Public Vault on Ethereum Mainnet deploys its funds into a HOT AMM liquidity pool ([details](../../arrakisModular/publicVaults.md#wethusdc-vault)).

This public vault offering is similar to LPing on a traditional AMM, but has a few advanced features under the hood:

- actively managed concentrated liquidity rebalancing (via the Arrakis Public Vault `manager` role)
- intents-based Quoter activity (via the underlying HOT AMM `QuoteSigner` role)

Thanks to these roles (and proper strategies for their activity), LPs can passively make WETH/USDC markets in a way that is competitive with the most sophisticated Private Market Makers onchain.
