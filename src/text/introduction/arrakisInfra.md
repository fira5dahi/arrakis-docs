# Arrakis Protocol

Arrakis Protocol consists of two major infrastructural components:

- Offchain Market Making Infrastructure
- Onchain Smart Contract Framework

Our smart contract framework for DEX integrations (Arrakis Modular) works together with our offchain market making infrastructure. The union of these onchain and offchain components comprise the Arrakis Protocol.

<p align="center">
<img src="../../../img/arrakis-infra-overview.svg" alt="arrakis-modular" width="500" class="img-svg"/>
</p>

For example, Arrakis Pro on [Uniswap V4](../modules/uniV4Module/overview.md) is formed by the following components:

- Arrakis Quoter and other offchain market making components to determine dynamic fees.
- Arrakis Modular (smart contract framework) Private Vaults.
- A new custom Arrakis Uniswap V4 Hook to give private access to a given pool as well as setting dynamic fees which are responsive to market conditions.
