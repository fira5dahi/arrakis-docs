# INFTSVG

*Interface for the NFTSVG contract*


## Functions
### isNFTSVG

Checks if the contract is compliant with the NFTSVG interface


```solidity
function isNFTSVG() external pure returns (bool);
```

### generateVaultURI

Generates a URI for a given vault


```solidity
function generateVaultURI(
    SVGParams memory params_
) external pure returns (string memory);
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`params_`|`SVGParams`|Parameters for generating the URI|


### generateFallbackURI

Generates a fallback URI for a given vault


```solidity
function generateFallbackURI(
    SVGParams memory params_
) external pure returns (string memory);
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`params_`|`SVGParams`|Parameters for generating the URI|


