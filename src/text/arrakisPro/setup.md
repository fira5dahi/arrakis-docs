# Arrakis Pro Vault Setup

## Deployment

For now simply [contact us](https://qxqhpatmzz7.typeform.com/to/IZdNgmmM?typeform-source=arrakis.finance) to have an Arrakis engineer deploy and configure an Arrakis Pro vault on your behalf.

At deployment you choose what initial **module** your vault uses. See [integrations](./integrations.md) section for more info.

## Deposit

After deployment, you can now deposit liquidity into your Arrakis Pro vault.

#### Deposit Using a Safe and Safe App:

Navigate to your vault owner Safe on [Safe App](https://app.safe.global). Then go to `Apps` and look for the official Arrakis Pro App. In the Safe app you will see your Pro vault(s) and can use the GUI to deposit with one multi-step Safe transaction.

#### Deposit Manually:

1. From `vault.owner()` acct -> call [whitelistDepositors](../../text/arrakisModular/technicalReference/metaVaults/privateVaults/contract.ArrakisMetaVaultPrivate.html#whitelistdepositors) on your Vault contract to whitelist the account that will deposit tokens (even owner has to explicitly whitelist itself before depositing).

2. From `whitelisted depositor` acct -> approve `vault.module()` contract address as spender of token(s) you will deposit.

3. From `whitelisted depositor` acct -> Call [deposit](../../text/arrakisModular/technicalReference/metaVaults/privateVaults/contract.ArrakisMetaVaultPrivate.html#deposit) on your Vault contract to deposit funds. (If depositing native ETH remember to pass a `msg.value` that matches the amount0/1 argument)

## Activation

After deposit your vault is not necessarily activated immediately. To activate your vault and deploy LP into the DEX of interest, you'll need a "strategy config" set on the Arrakis Pro Backend. See [strategies](../../text/arrakisPro/strategies/overview.md) section.
