# ICLGauge


## Functions
### nft


```solidity
function nft() external view returns (INonfungiblePositionManager);
```

### voter


```solidity
function voter() external view returns (IVoter);
```

### feesVotingReward


```solidity
function feesVotingReward() external view returns (address);
```

### periodFinish


```solidity
function periodFinish() external view returns (uint256);
```

### rewardRate


```solidity
function rewardRate() external view returns (uint256);
```

### rewards


```solidity
function rewards(
    uint256 tokenId
) external view returns (uint256);
```

### lastUpdateTime


```solidity
function lastUpdateTime(
    uint256 tokenId
) external view returns (uint256);
```

### rewardRateByEpoch


```solidity
function rewardRateByEpoch(
    uint256
) external view returns (uint256);
```

### fees0


```solidity
function fees0() external view returns (uint256);
```

### fees1


```solidity
function fees1() external view returns (uint256);
```

### WETH9


```solidity
function WETH9() external view returns (address);
```

### token0


```solidity
function token0() external view returns (address);
```

### token1


```solidity
function token1() external view returns (address);
```

### tickSpacing


```solidity
function tickSpacing() external view returns (int24);
```

### left


```solidity
function left() external view returns (uint256 _left);
```

### rewardToken


```solidity
function rewardToken() external view returns (address);
```

### isPool


```solidity
function isPool() external view returns (bool);
```

### supportsPayable


```solidity
function supportsPayable() external view returns (bool);
```

### rewardGrowthInside


```solidity
function rewardGrowthInside(
    uint256 tokenId
) external view returns (uint256);
```

### initialize


```solidity
function initialize(
    address _pool,
    address _feesVotingReward,
    address _rewardToken,
    address _voter,
    address _nft,
    address _token0,
    address _token1,
    int24 _tickSpacing,
    bool _isPool
) external;
```

### earned


```solidity
function earned(
    address account,
    uint256 tokenId
) external view returns (uint256);
```

### getReward


```solidity
function getReward(
    address account
) external;
```

### getReward


```solidity
function getReward(
    uint256 tokenId
) external;
```

### notifyRewardAmount


```solidity
function notifyRewardAmount(
    uint256 amount
) external;
```

### notifyRewardWithoutClaim


```solidity
function notifyRewardWithoutClaim(
    uint256 amount
) external;
```

### deposit


```solidity
function deposit(
    uint256 tokenId
) external;
```

### withdraw


```solidity
function withdraw(
    uint256 tokenId
) external;
```

### stakedValues


```solidity
function stakedValues(
    address depositor
) external view returns (uint256[] memory);
```

### stakedByIndex


```solidity
function stakedByIndex(
    address depositor,
    uint256 index
) external view returns (uint256);
```

### stakedContains


```solidity
function stakedContains(
    address depositor,
    uint256 tokenId
) external view returns (bool);
```

### stakedLength


```solidity
function stakedLength(
    address depositor
) external view returns (uint256);
```

## Events
### NotifyReward

```solidity
event NotifyReward(address indexed from, uint256 amount);
```

### Deposit

```solidity
event Deposit(
    address indexed user,
    uint256 indexed tokenId,
    uint128 indexed liquidityToStake
);
```

### Withdraw

```solidity
event Withdraw(
    address indexed user,
    uint256 indexed tokenId,
    uint128 indexed liquidityToStake
);
```

### ClaimFees

```solidity
event ClaimFees(
    address indexed from, uint256 claimed0, uint256 claimed1
);
```

### ClaimRewards

```solidity
event ClaimRewards(address indexed from, uint256 amount);
```

