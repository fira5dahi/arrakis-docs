# IAerodromeStandardModulePrivate

**Author:**
Arrakis Finance

Aerodrome Module interface, modules able to interact with aerodrome dex.


## Functions
### initialize

initialize function to delegate call onced the beacon proxy is deployed,
for initializing the aerodrome module.


```solidity
function initialize(
    IOracleWrapper oracle_,
    uint24 maxSlippage_,
    address aeroReceiver_,
    int24 tickSpacing_,
    address metaVault_
) external;
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`oracle_`|`IOracleWrapper`|oracle that will be the price reference.|
|`maxSlippage_`|`uint24`|maximum slippage allowed during swap, mint and burn.|
|`aeroReceiver_`|`address`|recevier of aero token belonging to manager.|
|`tickSpacing_`|`int24`|tickSpacing of the aero pool to interact with.|
|`metaVault_`|`address`|address of the meta vault|


### rebalance

function used to rebalance the inventory of the module.


```solidity
function rebalance(
    RebalanceParams calldata params_
) external;
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`params_`|`RebalanceParams`|params including decrease positions, swap, increase positions and mint datas.|


### claimRewards

function used by user to claim the aero rewards.


```solidity
function claimRewards(
    address receiver_
) external;
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`receiver_`|`address`|address that will receive the aero rewards.|


### claimManager

function used by executor to claim the manager aero rewards.


```solidity
function claimManager() external;
```

### approve

function used to approve a spender to use the left over of the module.


```solidity
function approve(
    address spender_,
    uint256 amount0_,
    uint256 amount1_
) external;
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`spender_`|`address`|address that will be allowed to use left over.|
|`amount0_`|`uint256`|amount of token0 allowed to be used by spender.|
|`amount1_`|`uint256`|amount of token1 allowed to be used by spender.|


### setReceiver

function used to set the receiver of aero rewards.


```solidity
function setReceiver(
    address newReceiver_
) external;
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`newReceiver_`|`address`|new address that will receive the aero token.|


### nftPositionManager

function used to get the NonFungiblePositionManager of aerodrome.


```solidity
function nftPositionManager()
    external
    view
    returns (INonfungiblePositionManager);
```

### factory

function used to get the factory of aerodrome.


```solidity
function factory() external view returns (IUniswapV3Factory);
```

### voter

function used to get the voter of aerodrome.


```solidity
function voter() external view returns (IVoter);
```

### tokenIds

function used to get the list of tokenIds of non fungible position.


```solidity
function tokenIds() external view returns (uint256[] memory);
```

### maxSlippage

function used to get the maximum slippage.


```solidity
function maxSlippage() external view returns (uint24);
```

### aeroReceiver

function used to get aero token receiver.


```solidity
function aeroReceiver() external view returns (address);
```

### pool

function used to get aero pool the module is interacting with.


```solidity
function pool() external view returns (address);
```

### gauge

function used to get aero gauge associated to pool the module is interacting with.


```solidity
function gauge() external view returns (address);
```

### aeroManagerBalance

function used to get aero balance due to manager.


```solidity
function aeroManagerBalance() external view returns (uint256);
```

### oracle

function used to get the oracle that
will be used to proctect rebalances.


```solidity
function oracle() external view returns (IOracleWrapper);
```

### AERO

function used to get aero token address.


```solidity
function AERO() external view returns (address);
```

## Events
### LogApproval
Event describing an approval of left overs to an address.


```solidity
event LogApproval(
    address indexed spender, uint256 amount0, uint256 amount1
);
```

**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`spender`|`address`|the address that will get the allowance.|
|`amount0`|`uint256`|the amount of token0 allowed to spender.|
|`amount1`|`uint256`|the amount of token1 allowed to spender.|

### LogRebalance
Event describing an rebalance results on underlying.


```solidity
event LogRebalance(
    uint256 burn0, uint256 burn1, uint256 mint0, uint256 mint1
);
```

**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`burn0`|`uint256`|the amount of token0 burned during rebalance.|
|`burn1`|`uint256`|the amount of token1 burned during rebalance.|
|`mint0`|`uint256`|the amount of token0 minted during rebalance.|
|`mint1`|`uint256`|the amount of token1 minted during rebalance.|

### LogClaim
Event describing an claim by user of aero token.


```solidity
event LogClaim(address indexed receiver, uint256 aeroAmount);
```

**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`receiver`|`address`|the receiver of aero token.|
|`aeroAmount`|`uint256`|the amount of aero token claimed.|

### LogManagerClaim
Event describing an claim by manager of aero token.


```solidity
event LogManagerClaim(address indexed receiver, uint256 aeroAmount);
```

**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`receiver`|`address`|the receiver of aero token.|
|`aeroAmount`|`uint256`|the amount of aero token claimed.|

### LogSetReceiver
Event describing the update of receiver of manager aero reward.


```solidity
event LogSetReceiver(address oldReceiver, address newReceiver);
```

**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`oldReceiver`|`address`|previous receiver of aero token.|
|`newReceiver`|`address`|new receiver of aero token.|

## Errors
### MaxSlippageGtTenPercent
*triggered when the max slippage variable is set to greater than 10%.*


```solidity
error MaxSlippageGtTenPercent();
```

### OnlyMetaVaultOwner
*triggered when the caller is different than the meta vault owner.*


```solidity
error OnlyMetaVaultOwner();
```

### NativeCoinNotSupported
*triggered when token pair contain native coin.*


```solidity
error NativeCoinNotSupported();
```

### BurnToken0
*triggered when burn of token0 is smaller than expected.*


```solidity
error BurnToken0();
```

### BurnToken1
*triggered when burn of token1 is smaller than expected.*


```solidity
error BurnToken1();
```

### MintToken0
*triggered when mint of token0 is smaller than expected.*


```solidity
error MintToken0();
```

### MintToken1
*triggered when mint of token1 is smaller than expected.*


```solidity
error MintToken1();
```

### TokenIdNotFound
*triggered when tokenId of position is unknown from the module.*


```solidity
error TokenIdNotFound();
```

### Token0Mismatch
*triggered when token0 of mintParams is different than module token0.*


```solidity
error Token0Mismatch();
```

### Token1Mismatch
*triggered when token1 of mintParams is different than module token1.*


```solidity
error Token1Mismatch();
```

### TickSpacingMismatch
*triggered when tick spacing of mintParams is different than the pool module.*


```solidity
error TickSpacingMismatch();
```

### ExpectedMinReturnTooLow
*triggered when min return of rebalance swap is too low.*


```solidity
error ExpectedMinReturnTooLow();
```

### WrongRouter
*triggered when swap router of the rebalance payload is unauthorized address.*


```solidity
error WrongRouter();
```

### SlippageTooHigh
*triggered when amount received from rebalance swap is too low.*


```solidity
error SlippageTooHigh();
```

### OverMaxDeviation
*triggered when deviation of pool price from oracle price is
greater than max allowed value.*


```solidity
error OverMaxDeviation();
```

### SameReceiver
*triggered when new aero receiver is equal to old aero receiver.*


```solidity
error SameReceiver();
```

### PoolNotFound
*triggered when pool has not been created on factory.*


```solidity
error PoolNotFound();
```

### AmountsZero
*triggered when funded amounts are equals to zero.*


```solidity
error AmountsZero();
```

### OnlyManagerOwner
*triggered when caller is not the owner of the manager.*


```solidity
error OnlyManagerOwner();
```

### AEROTokenNotSupported
*triggered when aero token is one of the token of the module token pair.*


```solidity
error AEROTokenNotSupported();
```

### GaugeKilled
*triggered when gauge returned by voter is not alive.*


```solidity
error GaugeKilled();
```

