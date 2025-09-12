# ISafe


## Functions
### execTransactionFromModule

*Allows a Module to execute a Safe transaction without any further confirmations.*


```solidity
function execTransactionFromModule(
    address to,
    uint256 value,
    bytes calldata data,
    Operation operation
) external returns (bool success);
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`to`|`address`|Destination address of module transaction.|
|`value`|`uint256`|Ether value of module transaction.|
|`data`|`bytes`|Data payload of module transaction.|
|`operation`|`Operation`|Operation type of module transaction.|


### execTransactionFromModuleReturnData


```solidity
function execTransactionFromModuleReturnData(
    address to,
    uint256 value,
    bytes calldata data,
    Operation operation
) external returns (bool success, bytes memory returnData);
```

### disableModule


```solidity
function disableModule(address prevModule, address module) external;
```

### getModulesPaginated


```solidity
function getModulesPaginated(
    address start,
    uint256 pageSize
) external view returns (address[] memory array, address next);
```

