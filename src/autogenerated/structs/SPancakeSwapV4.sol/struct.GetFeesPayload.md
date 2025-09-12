# GetFeesPayload


```solidity
struct GetFeesPayload {
    uint256 feeGrowthInside0Last;
    uint256 feeGrowthInside1Last;
    PoolId poolId;
    ICLPoolManager poolManager;
    uint128 liquidity;
    int24 tick;
    int24 lowerTick;
    int24 upperTick;
}
```

