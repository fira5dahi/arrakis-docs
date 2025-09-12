# IPancakeSwapV4StandardModule


## Functions
### initialize

initialize function to delegate call onced the beacon proxy is deployed,
for initializing the uniswap v4 standard module.

*this function will deposit fund as left over on poolManager.*


```solidity
function initialize(
    uint256 init0_,
    uint256 init1_,
    bool isInversed_,
    PoolKey calldata poolKey_,
    IOracleWrapper oracle_,
    uint24 maxSlippage_,
    address metaVault_
) external;
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`init0_`|`uint256`|initial amount of token0 to provide to uniswap standard module.|
|`init1_`|`uint256`|initial amount of token1 to provide to valantis module.|
|`isInversed_`|`bool`|boolean to check if the poolKey's currencies pair are inversed, compared to the module's tokens pair.|
|`poolKey_`|`PoolKey`|pool key of the uniswap v4 pool that will be used by the module.|
|`oracle_`|`IOracleWrapper`|address of the oracle used by the uniswap v4 standard module.|
|`maxSlippage_`|`uint24`|allowed to manager for rebalancing the inventory using swap.|
|`metaVault_`|`address`|address of the meta vault|


### approve


```solidity
function approve(
    address spender_,
    address[] calldata tokens_,
    uint256[] calldata amounts
) external;
```

### setPool

function used to set the pool for the module.


```solidity
function setPool(
    PoolKey calldata poolKey_,
    LiquidityRange[] calldata liquidityRanges_,
    SwapPayload calldata swapPayload_,
    uint256 minBurn0_,
    uint256 minBurn1_,
    uint256 minDeposit0_,
    uint256 minDeposit1_
) external;
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`poolKey_`|`PoolKey`|pool key of the uniswap v4 pool that will be used by the module.|
|`liquidityRanges_`|`LiquidityRange[]`|list of liquidity ranges to be used by the module on the new pool.|
|`swapPayload_`|`SwapPayload`|swap payload to be used during rebalance.|
|`minBurn0_`|`uint256`|minimum amount of token0 to burn.|
|`minBurn1_`|`uint256`|minimum amount of token1 to burn.|
|`minDeposit0_`|`uint256`|minimum amount of token0 to deposit.|
|`minDeposit1_`|`uint256`|minimum amount of token1 to deposit.|


### rebalance

function used to rebalance the inventory of the module.


```solidity
function rebalance(
    LiquidityRange[] calldata liquidityRanges_,
    SwapPayload memory swapPayload_,
    uint256 minBurn0_,
    uint256 minBurn1_,
    uint256 minDeposit0_,
    uint256 minDeposit1_
)
    external
    returns (
        uint256 amount0Minted,
        uint256 amount1Minted,
        uint256 amount0Burned,
        uint256 amount1Burned
    );
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`liquidityRanges_`|`LiquidityRange[]`|list of liquidity ranges to be used by the module.|
|`swapPayload_`|`SwapPayload`|swap payload to be used during rebalance.|
|`minBurn0_`|`uint256`|minimum amount of token0 to burn.|
|`minBurn1_`|`uint256`|minimum amount of token1 to burn.|
|`minDeposit0_`|`uint256`|minimum amount of token0 to deposit.|
|`minDeposit1_`|`uint256`|minimum amount of token1 to deposit.|

**Returns**

|Name|Type|Description|
|----|----|-----------|
|`amount0Minted`|`uint256`|amount of token0 minted.|
|`amount1Minted`|`uint256`|amount of token1 minted.|
|`amount0Burned`|`uint256`|amount of token0 burned.|
|`amount1Burned`|`uint256`|amount of token1 burned.|


### withdrawEth

function used to withdraw eth from the module.

*these fund will be used to swap eth to the other token
of the currencyPair to rebalance the inventory inside a single tx.*


```solidity
function withdrawEth(
    uint256 amount_
) external;
```

### poolManager

function used to get the uniswap v4 pool manager.


```solidity
function poolManager() external view returns (ICLPoolManager);
```
**Returns**

|Name|Type|Description|
|----|----|-----------|
|`<none>`|`ICLPoolManager`|poolManager return the pool manager.|


### isInversed

function used to know if the poolKey's currencies pair are inversed.


```solidity
function isInversed() external view returns (bool);
```

### vault


```solidity
function vault() external view returns (IVault);
```

### poolKey

function used to get the pool's key of the module.


```solidity
function poolKey()
    external
    view
    returns (
        Currency currency0,
        Currency currency1,
        IHooks hooks,
        IPoolManager poolManager,
        uint24 fee,
        bytes32 parameters
    );
```

### oracle

function used to get the oracle that
will be used to proctect rebalances.


```solidity
function oracle() external view returns (IOracleWrapper);
```

### maxSlippage

function used to get the max slippage that
can occur during swap rebalance.


```solidity
function maxSlippage() external view returns (uint24);
```

### getRanges

function used to get the list of active ranges.


```solidity
function getRanges() external view returns (Range[] memory ranges);
```
**Returns**

|Name|Type|Description|
|----|----|-----------|
|`ranges`|`Range[]`|active ranges|


## Events
### LogApproval

```solidity
event LogApproval(
    address indexed spender, address[] tokens, uint256[] amounts
);
```

### LogRebalance

```solidity
event LogRebalance(
    LiquidityRange[] liquidityRanges,
    uint256 amount0Minted,
    uint256 amount1Minted,
    uint256 amount0Burned,
    uint256 amount1Burned
);
```

### LogSetPool

```solidity
event LogSetPool(PoolKey oldPoolKey, PoolKey poolKey);
```

### LogSetRewardReceiver

```solidity
event LogSetRewardReceiver(address rewardReceiver);
```

## Errors
### Currency0DtToken0

```solidity
error Currency0DtToken0(address currency0, address token0);
```

### Currency1DtToken1

```solidity
error Currency1DtToken1(address currency1, address token1);
```

### Currency1DtToken0

```solidity
error Currency1DtToken0(address currency1, address token0);
```

### Currency0DtToken1

```solidity
error Currency0DtToken1(address currency0, address token1);
```

### RangeShouldBeActive

```solidity
error RangeShouldBeActive(int24 tickLower, int24 tickUpper);
```

### SqrtPriceZero

```solidity
error SqrtPriceZero();
```

### OverBurning

```solidity
error OverBurning();
```

### MaxSlippageGtTenPercent

```solidity
error MaxSlippageGtTenPercent();
```

### NativeCoinCannotBeToken1

```solidity
error NativeCoinCannotBeToken1();
```

### NoRemoveOrAddLiquidityHooks

```solidity
error NoRemoveOrAddLiquidityHooks();
```

### OnlyMetaVaultOwner

```solidity
error OnlyMetaVaultOwner();
```

### InsufficientFunds

```solidity
error InsufficientFunds();
```

### OverMaxDeviation

```solidity
error OverMaxDeviation();
```

### AmountZero

```solidity
error AmountZero();
```

### BurnToken0

```solidity
error BurnToken0();
```

### BurnToken1

```solidity
error BurnToken1();
```

### MintToken0

```solidity
error MintToken0();
```

### MintToken1

```solidity
error MintToken1();
```

### SamePool

```solidity
error SamePool();
```

### ExpectedMinReturnTooLow

```solidity
error ExpectedMinReturnTooLow();
```

### InvalidCurrencyDelta

```solidity
error InvalidCurrencyDelta();
```

### WrongRouter

```solidity
error WrongRouter();
```

### SlippageTooHigh

```solidity
error SlippageTooHigh();
```

### InvalidMsgValue

```solidity
error InvalidMsgValue();
```

### OnlyVault

```solidity
error OnlyVault();
```

### TicksMisordered

```solidity
error TicksMisordered(int24 tickLower, int24 tickUpper);
```

### TickLowerOutOfBounds

```solidity
error TickLowerOutOfBounds(int24 tickLower);
```

### TickUpperOutOfBounds

```solidity
error TickUpperOutOfBounds(int24 tickUpper);
```

### OnlyManagerOrVaultOwner

```solidity
error OnlyManagerOrVaultOwner();
```

### LengthsNotEqual

```solidity
error LengthsNotEqual();
```

### SameRewardReceiver

```solidity
error SameRewardReceiver();
```

## Structs
### Range

```solidity
struct Range {
    int24 tickLower;
    int24 tickUpper;
}
```

### LiquidityRange

```solidity
struct LiquidityRange {
    Range range;
    int128 liquidity;
}
```

