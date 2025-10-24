# Quoter

A crucial offchain component of the HOT AMM is the `QuoteSigner` role which is set directly on the `HOT.sol` valantis ALM smart contract containing the core pricing logic of the HOT AMM.

Whoever holds the private key to the `QuoteSigner` role has the authority to at any time issue a signed quote that allows the recipient to execute a swap directly against the funds in the liquidity pool at the price specified in the signed quote (subject to certain onchain safety checks on the price and volume of the quote).

For Arrakis Public Vaults, the _Quoter_ is a semi-trusted automated offchain process, which escrows Public Vault `QuoteSigner` keys and signs quotes to integrated parties (like CoWSwap solvers) at prices determined by the state of centralized exchanges, state of the LP Vault's onchain reserves, and the current Requests-For-Quotes seeking to trade.

## Quoter Market Making Strategy

A quoter can use any offchain quoting strategy, as long as it's within the bounds enforced at the smart contract level: 
- bounds on size of any quote
- bounds on number of quotes in a block
- bounds on quote prices compared to an onchain oracle

A _manager_ on the `HOT.sol` smart contract can set both the `QuoteSigner` role and these bounds on the `QuoteSigner` activity (this role should be burned, timelocked, or otherwise trusted). Within these guardrails, a quoter can implement any strategy it likes to issue quotes (and signed quote holders can execute these valid quotes).

The ETH/USDC Public Vault Quoter uses an Avellaneda and Stoikov based approach, where the bid ask spread skews around the mid market price with the goal to converge to a target inventory ratio (in this case, 50% ETH and 50% USDC).

## Quoter Oracle Values

When the `QuoteSigner` issues signed quotes they can attach metadata that acts as oracle values to the state of the onchain AMM if and when the quote gets executed onchain. The key values are:

- a new value for the midprice of the AMM, based on the Quoter's current instantaneous midprice observed offchain (`sqrtSpotPriceX96New`)
- a new starting value for swap fee rates (`feeMinToken{0,1}`)
- a new growth rate for swap fees (`feeGrowthE6Token{0,1}`)
- a new max swap fee for the fee growth to stop at (`feeMaxToken{0,1}`)

When a quote actually executes onchain (and is the first one to do so in a block) it will _automatically_ reset the state of the AMM from that point in the block onward to:

- spot price at `sqrtSpotPriceX96New`
- swap fee for token{0,1} of `feeMinToken{0,1} + feeGrowthE6Token{0,1} * (blockTimestamp- signatureTimestamp) / 100` (the minimum fee, plus the growth rate for the amount of time that has elapsed since this quote was signed)

If no new signed quotes land at the top of the next block then the swap fee rates will continue to grow second by second at the linear rate and thus will be larger at the top of the next block. This swap fee growth continues until the fee hits the maximum rate or until a new signed quote lands and resets the process.

## Quoter Decentralization

One major direction of research and development at Arrakis is to make the Public Vault _Quoter_ more transparently verifiable and trustless. More info on that coming soon!
