# Uniswap V4 Module

Arrakis Private Vault module integration with Uniswap V4.

Vault Type(s): Private Vault

Features:

- manage multiple V4 liquidity positions in an aggregated/batched way with nice interfaces
- configure and control automated LP strategies tailor designed for V4
- easily migrate liquidity from one Uniswap V4 hook to another (or algorithmically switch between them)
- integrates [merkl rewards](https://app.merkl.xyz/) if there are auxiliary rewards for LPing that pair
- optionally enable direct RFQ with the vault (policed by your oracle of choice)
- optionally use ArrakisProHook liquidity pool to automate dynamic swap fees with Arrakis

See full contract specification [here](../../text/arrakisModular/technicalReference/modules/implementations/abstract.UniV4StandardModule.md) and [here](../../text/arrakisModular/technicalReference/modules/implementations/contract.UniV4StandardModulePrivate.md)

## Deployments

Networks: Ethereum Mainnet, Base, Arbitrum, Unichain, Optimism Mainnet

