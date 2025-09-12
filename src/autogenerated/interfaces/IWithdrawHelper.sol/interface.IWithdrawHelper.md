# IWithdrawHelper


## Functions
### withdraw

Withdraws the funds from the vault at any ratio.


```solidity
function withdraw(
    address safe_,
    address vault_,
    uint256 amount0_,
    uint256 amount1_,
    address payable receiver_
) external;
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`safe_`|`address`|The address of the safe that owns the vault.|
|`vault_`|`address`|The address of the vault to withdraw the funds from.|
|`amount0_`|`uint256`|The amount of token0 to withdraw.|
|`amount1_`|`uint256`|The amount of token1 to withdraw.|
|`receiver_`|`address payable`|The address that will receive the funds.|


## Errors
### InsufficientUnderlying
Error emitted when the withdraw try to
withdraw more than the funds sitting on the vault.


```solidity
error InsufficientUnderlying();
```

### Unauthorized
Error emitted when the caller is not the safe.


```solidity
error Unauthorized();
```

### WithdrawErr
Error emitted when the withdraw fails.


```solidity
error WithdrawErr();
```

### WhitelistDepositorErr
Error emitted when whitelisting safe as depositor fails.


```solidity
error WhitelistDepositorErr();
```

### Transfer0Err
Error emitted when transfering token0 to receiver fails.


```solidity
error Transfer0Err();
```

### Transfer1Err
Error emitted when transfering token1 to receiver fails.


```solidity
error Transfer1Err();
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

