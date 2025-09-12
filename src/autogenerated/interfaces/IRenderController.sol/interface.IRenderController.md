# IRenderController


## Functions

### setRenderer

function used to set the renderer contract adress

_only the owner can do it._

```solidity
function setRenderer(address renderer_) external;
```

**Parameters**

| Name        | Type      | Description                                                                   |
| ----------- | --------- | ----------------------------------------------------------------------------- |
| `renderer_` | `address` | address of the contract that will render the tokenUri for the svg of the nft. |

### isNFTSVG

_for knowning if renderer is a NFTSVG contract._

```solidity
function isNFTSVG(address renderer_) external view returns (bool);
```

### renderer

NFTSVG contract that will generate the tokenURI.

```solidity
function renderer() external view returns (address);
```

## Events

### LogSetRenderer

```solidity
event LogSetRenderer(address newRenderer);
```

## Errors

### InvalidRenderer

```solidity
error InvalidRenderer();
```

### AddressZero

```solidity
error AddressZero();
```
