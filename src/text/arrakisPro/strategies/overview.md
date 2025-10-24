# Strategies

Arrakis Pro offers adaptive strategies designed for efficient on-chain liquidity management. These strategies work for all AMMs that are based on Uniswap V3 Math, including Uniswap V4, Aerodrome, Velodrome, and PancakeSwap V4.

- The [Bootstrap Strategy](bootstrap.md) is ideal for token launches with imbalanced starting inventories. It deploys liquidity across a full-range position and several narrow “bootstrapping” ranges that hold mostly "base" tokens (as opposed to "quote" tokens like USDC or ETH). As users trade, the strategy captures volatility asymmetrically—accumulating more quote token on buy pressure—and steadily moves toward a 50/50 token balance. Once ~50/50 balance is reached, the strategy stops

- The [Flagship Strategy](flagship.md) manages mature pools by reacting to price shifts, inventory imbalance, and volatility. It operates in three risk modes adjusting liquidity depth and range width accordingly. During calm markets, it concentrates liquidity to maximize fees and reduce price impact. During volatile markets, it widens ranges and reduces exposure. Rebalancing is based on price and inventory trends, ensuring stability and efficiency.

Together, these strategies guide tokens from launch to maturity. On the one hand, they provide consistent price impact for traders. On the other hand, they ensure a stable inventory balance and fee generation for treasuries.

We are continuously designing tailored strategies for specific token pairs, which may need more frequent rebalances, swapping on third party aggregators or using offchain prediction models, among others.