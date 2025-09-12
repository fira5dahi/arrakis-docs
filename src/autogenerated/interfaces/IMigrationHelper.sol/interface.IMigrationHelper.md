# IMigrationHelper

## Functions
### migrateVault

Migrate a vault from ArrakisV2 to ArrakisMetaVaultPrivate.

*can be called by the owner of this migration helper or by the safe.*


```solidity
function migrateVault(
    Migration calldata params_
) external returns (address vault);
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`params_`|`Migration`|Migration struct, containing informations about how to migrate from ArrakisV2 vault to a modular vault.|

**Returns**

|Name|Type|Description|
|----|----|-----------|
|`vault`|`address`|address of the new ArrakisMetaVaultPrivate vault.|


### palmTerms

Get the address of the arrakisV2 PALMTerms contract.


```solidity
function palmTerms() external view returns (address);
```

### factory

Get the address of the arrakis modular meta vault factory.


```solidity
function factory() external view returns (address);
```

### manager

Get the address of the arrakis standard manager.


```solidity
function manager() external view returns (address);
```

### poolManager

Get the address of the uni v4 pool manager.


```solidity
function poolManager() external view returns (address);
```

### weth

Get the address of the WETH.


```solidity
function weth() external view returns (address);
```

## Errors
### AddressZero
Error emitted when the address is zero.


```solidity
error AddressZero();
```

### CloseTermsErr
Error emitted when closing arrakisV2 vault fails.


```solidity
error CloseTermsErr();
```

### WhitelistDepositorErr
Error emitted when whitelisting safe as depositor fails.


```solidity
error WhitelistDepositorErr();
```

### Approval0Err
Error emitted when approving module to use token0 fails.


```solidity
error Approval0Err();
```

### Approval1Err
Error emitted when approving module to use token1 fails.


```solidity
error Approval1Err();
```

### DepositErr
Error emitted when depositing through the safe fails.


```solidity
error DepositErr();
```

### RebalanceErr
Error emitted when rebalancing the new ArrakisMetaVaultPrivate fails.


```solidity
error RebalanceErr();
```

### ChangeExecutorErr
Error emitted when updating the executor fails.


```solidity
error ChangeExecutorErr();
```

### WithdrawETH
Error emitted when withdrawing ETH from WETH sm fails.


```solidity
error WithdrawETH();
```

### InvalidSqrtPrice
Error emitted when pool creation fails due to initial sqrtPrice not provided by payload.


```solidity
error InvalidSqrtPrice();
```

### VaultCreationErr
Error emitted when vault creation fails.


```solidity
error VaultCreationErr();
```

### UnableModuleErr
Error emitted when disable module fails.


```solidity
error UnableModuleErr();
```

### PayloadOutdated
Error emitted when the new uni V4 pool creation with an outdated price.


```solidity
error PayloadOutdated();
```

## Structs
### InternalStruct

```solidity
struct InternalStruct {
    bytes payload;
    bool success;
    address token0;
    address token1;
    uint256 amount0;
    uint256 amount1;
    uint256 value;
    bool isInversed;
}
```

### CloseTerm
Struct containing informations about the close term.


```solidity
struct CloseTerm {
    IArrakisV2 vault;
    address newOwner;
    address newManager;
}
```

### PoolCreation
Struct containing informations about the v4 Pool
that should be used on the new vault. If createPool is true,
the pool will be created.


```solidity
struct PoolCreation {
    PoolKey poolKey;
    uint160 sqrtPriceX96;
}
```

### VaultCreation
Struct containing informations about the new
ArrakisMetaVaultPrivate vault to be created.


```solidity
struct VaultCreation {
    bytes32 salt;
    address upgradeableBeacon;
    uint256 init0;
    uint256 init1;
    IOracleWrapper oracle;
    bool isUniV4OracleNeedInitilization;
    uint24 maxDeviation;
    uint256 cooldownPeriod;
    address stratAnnouncer;
    uint24 maxSlippage;
}
```

### Migration
Struct containing informations about the migration.


```solidity
struct Migration {
    address safe;
    CloseTerm closeTerm;
    PoolCreation poolCreation;
    VaultCreation vaultCreation;
    bytes[] rebalancePayloads;
    address executor;
    uint256 timestampLimit;
}
```

