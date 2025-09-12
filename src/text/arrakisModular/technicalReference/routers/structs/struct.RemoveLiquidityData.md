# RemoveLiquidityData


```solidity
struct RemoveLiquidityData {
    uint256 burnAmount;
    uint256 amount0Min;
    uint256 amount1Min;
    address vault;
    address payable receiver;
}
```

**Variables**

| Name         | Type              | Description                                         |
| ------------ | ----------------- | --------------------------------------------------- |
| `burnAmount` | `uint256`         | Amount of vault shares to be burned by `msg.sender` |
| `amount0Min` | `uint256`         | Minimum amount of token0 to be send to `receiver`   |
| `amount1Min` | `uint256`         | Minimum amount of token1 to be send to `receiver`   |
| `vault`      | `address`         | Address of the vault to remove liquidity from       |
| `receiver`   | `payable address` | Address of the receiver of token0 and token1        |
