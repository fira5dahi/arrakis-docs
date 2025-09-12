# AddLiquidityData


```solidity
struct AddLiquidityData {
    uint256 amount0Max;
    uint256 amount1Max;
    uint256 amount0Min;
    uint256 amount1Min;
    uint256 amountSharesMin;
    address vault;
    address receiver;
}
```

**Variables**

| Name              | Type      | Description                                                               |
| ----------------- | --------- | ------------------------------------------------------------------------- |
| `amount0Max`      | `uint256` | Maximum amount of token0 to be transferred from `msg.sender` to the vault |
| `amount1Max`      | `uint256` | Maximum amount of token1 to be transferred from `msg.sender` to the vault |
| `amount0Min`      | `uint256` | Minimum amount of token0 to be transferred from `msg.sender` to the vault |
| `amount1Min`      | `uint256` | Minimum amount of token1 to be transferred from `msg.sender` to the vault |
| `amountSharesMin` | `uint256` | Minimum amount of vault shares to be received by `receiver`               |
| `vault`           | `address` | Address of the vault to add liquidity to                                  |
| `receiver`        | `address` | Address of the receiver of the vault shares                               |
