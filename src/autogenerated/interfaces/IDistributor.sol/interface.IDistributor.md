# IDistributor


## Functions
### claim

Claims rewards for a given set of users

*Unless another address has been approved for claiming, only an address can claim for itself*


```solidity
function claim(
    address[] calldata users,
    address[] calldata tokens,
    uint256[] calldata amounts,
    bytes32[][] calldata proofs
) external;
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`users`|`address[]`|Addresses for which claiming is taking place|
|`tokens`|`address[]`|ERC20 token claimed|
|`amounts`|`uint256[]`|Amount of tokens that will be sent to the corresponding users|
|`proofs`|`bytes32[][]`|Array of hashes bridging from a leaf `(hash of user | token | amount)` to the Merkle root|


### toggleOperator

Toggles whitelisting for a given user and a given operator

*When an operator is whitelisted for a user, the operator can claim rewards on behalf of the user*


```solidity
function toggleOperator(address user, address operator) external;
```

