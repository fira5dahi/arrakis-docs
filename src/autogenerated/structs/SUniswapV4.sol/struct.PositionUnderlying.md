# PositionUnderlying


```solidity
struct PositionUnderlying {
    uint160 sqrtPriceX96;
    IPoolManager poolManager;
    PoolKey poolKey;
    address self;
    int24 lowerTick;
    int24 upperTick;
}
```

