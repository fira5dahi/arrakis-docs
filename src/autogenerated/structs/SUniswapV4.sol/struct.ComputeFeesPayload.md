# ComputeFeesPayload


```solidity
struct ComputeFeesPayload {
    uint256 feeGrowthInsideLast;
    uint256 feeGrowthOutsideLower;
    uint256 feeGrowthOutsideUpper;
    uint256 feeGrowthGlobal;
    IPoolManager poolManager;
    PoolKey poolKey;
    uint128 liquidity;
    int24 tick;
    int24 lowerTick;
    int24 upperTick;
}
```

