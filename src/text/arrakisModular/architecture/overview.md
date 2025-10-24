# Architecture

[Meta Vault](../architecture/metaVaults.md): At the heart of the Arrakis Modular system is the concept of a Meta Vault. The Meta Vault creates a unified standard for providing two-sided liquidity to DEXs regardless of the particular features or interfaces of a given DEX.

[Modules](../architecture/modules.md): Each Meta Vault has the capability to whitelist various modules. A module is essentially a smart contract that establishes an integration with a liquidity-consuming dApp.

[Configuration](../architecture/configuration.md): Each Meta Vault is configurable by the Vault `owner`. This design ensures that as new DEXs emerge, Arrakis integration becomes a matter of simply creating and whitelisting a new module compatible with the DEX, and then activating it.

[Diagram](../architecture/diagram.md): Arrakis Modular smart contract system represented visually.

[Security](../architecture/security.md): Arrakis Modular from a Security POV.
