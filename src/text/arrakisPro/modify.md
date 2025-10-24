# Pro Vault Maintenance

> _NOTE: most maintenance actions are not yet available on the Arrakis Pro UI. But they will be soon. For now if urgent maintenance actions are needed follow this guide._


## updateVaultInfo

On the ArraksStandardManager every vault `owner` has the ability to adjust important management parameters for their vault.

1. View call `manager.vaultInfo(address vault)` to see current vault info.

2. from vault `owner` acct -> call `manager.updateVaultInfo(struct memory SetupParams)` [see here](../../text/arrakisModular/technicalReference/metaVaults/core/contract.ArrakisStandardManager.md#updatevaultinfo) where the struct has these fields:

```solidity
struct SetupParams {
    address vault;
    IOracleWrapper oracle;
    uint24 maxDeviation;
    uint256 cooldownPeriod;
    address executor;
    address stratAnnouncer;
    uint24 maxSlippagePIPS;
}
```

edit the fields you want to change and copy over the fields from Step 1 that you want to keep the same.

- `vault` that is the address of your vault. call will fail if msg.sender is not owner of this vault
- `oracle` is a smart contract which acts as onchain oracle to police executor actions. Read more about [Arrakis Price Oracles](../../text/arrakisModular/priceOracles.md)
- `maxDeviation` this is max deviation underlying module spot market can have from oracle price (in pips)
- `cooldownPeriod` shortest amount of seconds between any successful management actions on the vault
- `executor` account which can call management functions for this vault. Pro vaults have `0x420966bCf2A0351F26048cD07076627Cde4f79ac` as executor (the Arrakis Pro Backend)
- `stratAnnouncer` currently unused for now, (in future, account with ability to set vault offchain strategy config via onchain call)
- `maxSlippagePIPS` maximum slippage from oracle price on management swap actions (in pips)

The ArrakisStandardManager is deployed to address `0x2e6E879648293e939aA68bA4c6c129A1Be733bDA` on all networks. See mainnet contract onchain: [here](https://etherscan.io/address/0x2e6E879648293e939aA68bA4c6c129A1Be733bDA#readProxyContract)

## transfer vault

<div class="warning">
<b>WARNING: IF YOU TRANSFER A PRIVATE VAULT NFT YOU ALSO TRANSFER THE RIGHT TO WITHDRAW THE UNDERLYING FUNDS</b> (exactly like Uni V3 NFTs)
</div>

nevertheless you may want to migrate your Arrakis Pro vault to a new owner account. This is as simple as transferring the NFT to the target recipient which can usually be done on any wallet UI directly.

manual steps:

Find your token id of interest and call `transferFrom(address from, address to, uint256 tokenId)` on the PrivateVaultNFT contract. 

- The `from` is current `owner` of tokenId and also the acct you are calling from
- The `to` is your desired recipient of vault control
- The `tokenId` is the tokenId you found. It is also the `keccak256(vaultAddress)`

Arrakis PrivateVaultNFT contract is deployed to address `0x44A801e7E2E073bd8bcE4bCCf653239Fa156B762` on all networks. See mainnet contract onchain: [here](https://etherscan.io/address/0x44A801e7E2E073bd8bcE4bCCf653239Fa156B762#code)

## whitelistModules

Every vault `owner` has the ability to call `whitelistModules(address[] calldata beacons, bytes[] calldata datas)` [see here](../../../text/arrakisModular/technicalReference/metaVaults/core/abstract.ArrakisMetaVault.html#whitelistmodules)

with _valid module beacon addresses_ in the `beacons` argument and _valid module initialization payloads_ in the datas argument. 

Because these may not be simple calls to construct correctly, we recommend reaching out to Arrakis engineers if you want to whitelist new modules.