# INonfungiblePositionManager


## Functions
### mint


```solidity
function mint(
    MintParams calldata params
)
    external
    payable
    returns (
        uint256 tokenId,
        uint128 liquidity,
        uint256 amount0,
        uint256 amount1
    );
```

### increaseLiquidity


```solidity
function increaseLiquidity(
    IncreaseLiquidityParams calldata params
)
    external
    payable
    returns (uint128 liquidity, uint256 amount0, uint256 amount1);
```

### decreaseLiquidity


```solidity
function decreaseLiquidity(
    DecreaseLiquidityParams calldata params
) external payable returns (uint256 amount0, uint256 amount1);
```

### collect


```solidity
function collect(
    CollectParams calldata params
) external payable returns (uint256 amount0, uint256 amount1);
```

### burn


```solidity
function burn(
    uint256 tokenId
) external payable;
```

### positions


```solidity
function positions(
    uint256 tokenId
)
    external
    view
    returns (
        uint96 nonce,
        address operator,
        address token0,
        address token1,
        int24 tickSpacing,
        int24 tickLower,
        int24 tickUpper,
        uint128 liquidity,
        uint256 feeGrowthInside0LastX128,
        uint256 feeGrowthInside1LastX128,
        uint128 tokensOwed0,
        uint128 tokensOwed1
    );
```

### approve


```solidity
function approve(address to, uint256 tokenId) external;
```

## Structs
### MintParams

```solidity
struct MintParams {
    address token0;
    address token1;
    int24 tickSpacing;
    int24 tickLower;
    int24 tickUpper;
    uint256 amount0Desired;
    uint256 amount1Desired;
    uint256 amount0Min;
    uint256 amount1Min;
    address recipient;
    uint256 deadline;
    uint160 sqrtPriceX96;
}
```

### IncreaseLiquidityParams

```solidity
struct IncreaseLiquidityParams {
    uint256 tokenId;
    uint256 amount0Desired;
    uint256 amount1Desired;
    uint256 amount0Min;
    uint256 amount1Min;
    uint256 deadline;
}
```

### DecreaseLiquidityParams

```solidity
struct DecreaseLiquidityParams {
    uint256 tokenId;
    uint128 liquidity;
    uint256 amount0Min;
    uint256 amount1Min;
    uint256 deadline;
}
```

### CollectParams

```solidity
struct CollectParams {
    uint256 tokenId;
    address recipient;
    uint128 amount0Max;
    uint128 amount1Max;
}
```

