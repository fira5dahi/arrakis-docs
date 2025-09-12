# SwapData


```solidity
struct SwapData {
    bytes swapPayload;
    uint256 amountInSwap;
    uint256 amountOutSwap;
    address swapRouter;
    bool zeroForOne;
}
```

**Variables**

| Name            | Type      | Description                                                                                   |
| --------------- | --------- | --------------------------------------------------------------------------------------------- |
| `swapPayload`   | `bytes`   | Payload to use for a swap in an external venue. Transaction must be atomic                    |
| `amountInSwap`  | `uint256` | Amount of token to be swapped                                                                 |
| `amountOutSwap` | `uint256` | Minimum amount of the other token to be received from the swap                                |
| `swapRouter`    | `address` | Address of the router to be used for the swap                                                 |
| `zeroForOne`    | `bool`    | Boolean to determine the direction of the swap. If true swaps token0 for token1 and viceversa |
