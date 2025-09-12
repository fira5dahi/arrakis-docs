# IArrakisMetaVault


IArrakisMetaVault is a vault that is able to invest dynamically deposited
tokens into protocols through his module.

## Functions

### initialize

function used to initialize default module.

```solidity
function initialize(address module_) external;
```

**Parameters**

| Name      | Type      | Description                    |
| --------- | --------- | ------------------------------ |
| `module_` | `address` | address of the default module. |

### setModule

function used to set module

```solidity
function setModule(
    address module_,
    bytes[] calldata payloads_
) external;
```

**Parameters**

| Name        | Type      | Description                                     |
| ----------- | --------- | ----------------------------------------------- |
| `module_`   | `address` | address of the new module                       |
| `payloads_` | `bytes[]` | datas to initialize/rebalance on the new module |

### whitelistModules

function used to whitelist modules that can used by manager.

```solidity
function whitelistModules(
    address[] calldata beacons_,
    bytes[] calldata data_
) external;
```

**Parameters**

| Name       | Type        | Description                                             |
| ---------- | ----------- | ------------------------------------------------------- |
| `beacons_` | `address[]` | array of beacons addresses to use for modules creation. |
| `data_`    | `bytes[]`   | array of payload to use for modules creation.           |

### blacklistModules

function used to blacklist modules that can used by manager.

```solidity
function blacklistModules(address[] calldata modules_) external;
```

**Parameters**

| Name       | Type        | Description                                  |
| ---------- | ----------- | -------------------------------------------- |
| `modules_` | `address[]` | array of module addresses to be blacklisted. |

### whitelistedModules

function used to get the list of modules whitelisted.

```solidity
function whitelistedModules()
    external
    view
    returns (address[] memory modules);
```

**Returns**

| Name      | Type        | Description                    |
| --------- | ----------- | ------------------------------ |
| `modules` | `address[]` | whitelisted modules addresses. |

### totalUnderlying

function used to get the amount of token0 and token1 sitting
on the position.

```solidity
function totalUnderlying()
    external
    view
    returns (uint256 amount0, uint256 amount1);
```

**Returns**

| Name      | Type      | Description                                   |
| --------- | --------- | --------------------------------------------- |
| `amount0` | `uint256` | the amount of token0 sitting on the position. |
| `amount1` | `uint256` | the amount of token1 sitting on the position. |

### totalUnderlyingAtPrice

function used to get the amounts of token0 and token1 sitting
on the position for a specific price.

```solidity
function totalUnderlyingAtPrice(uint160 priceX96)
    external
    view
    returns (uint256 amount0, uint256 amount1);
```

**Parameters**

| Name       | Type      | Description                                               |
| ---------- | --------- | --------------------------------------------------------- |
| `priceX96` | `uint160` | price at which we want to simulate our tokens composition |

**Returns**

| Name      | Type      | Description                                                |
| --------- | --------- | ---------------------------------------------------------- |
| `amount0` | `uint256` | the amount of token0 sitting on the position for priceX96. |
| `amount1` | `uint256` | the amount of token1 sitting on the position for priceX96. |

### getInits

function used to get the initial amounts needed to open a position.

```solidity
function getInits()
    external
    view
    returns (uint256 init0, uint256 init1);
```

**Returns**

| Name    | Type      | Description                                     |
| ------- | --------- | ----------------------------------------------- |
| `init0` | `uint256` | the amount of token0 needed to open a position. |
| `init1` | `uint256` | the amount of token1 needed to open a position. |

### token0

function used to get the address of token0.

```solidity
function token0() external view returns (address);
```

### token1

function used to get the address of token1.

```solidity
function token1() external view returns (address);
```

### manager

function used to get manager address.

```solidity
function manager() external view returns (address);
```

### module

function used to get module used to
open/close/manager a position.

```solidity
function module() external view returns (IArrakisLPModule);
```

### moduleRegistry

function used to get module registry.

```solidity
function moduleRegistry() external view returns (address registry);
```

**Returns**

| Name       | Type      | Description                 |
| ---------- | --------- | --------------------------- |
| `registry` | `address` | address of module registry. |

## Events

### LogWithdrawManagerBalance

Event describing a manager fee withdrawal.

```solidity
event LogWithdrawManagerBalance(uint256 amount0, uint256 amount1);
```

**Parameters**

| Name      | Type      | Description                                                      |
| --------- | --------- | ---------------------------------------------------------------- |
| `amount0` | `uint256` | amount of token0 that manager has earned and will be transfered. |
| `amount1` | `uint256` | amount of token1 that manager has earned and will be transfered. |

### LogSetManager

Event describing owner setting the manager.

```solidity
event LogSetManager(address manager);
```

**Parameters**

| Name      | Type      | Description                                        |
| --------- | --------- | -------------------------------------------------- |
| `manager` | `address` | address of manager that will manage the portfolio. |

### LogSetModule

Event describing manager setting the module.

```solidity
event LogSetModule(address module, bytes[] payloads);
```

**Parameters**

| Name       | Type      | Description                                                 |
| ---------- | --------- | ----------------------------------------------------------- |
| `module`   | `address` | address of the new active module.                           |
| `payloads` | `bytes[]` | data payloads for initializing positions on the new module. |

### LogSetFirstModule

Event describing default module that the vault will be initialized with.

```solidity
event LogSetFirstModule(address module);
```

**Parameters**

| Name     | Type      | Description                    |
| -------- | --------- | ------------------------------ |
| `module` | `address` | address of the default module. |

### LogWhiteListedModules

Event describing list of modules that has been whitelisted by owner.

```solidity
event LogWhiteListedModules(address[] modules);
```

**Parameters**

| Name      | Type        | Description                                                                              |
| --------- | ----------- | ---------------------------------------------------------------------------------------- |
| `modules` | `address[]` | list of addresses corresponding to new modules now available to be activated by manager. |

### LogWhitelistedModule

Event describing whitelisted of the first module during vault creation.

```solidity
event LogWhitelistedModule(address module);
```

**Parameters**

| Name     | Type      | Description         |
| -------- | --------- | ------------------- |
| `module` | `address` | default activation. |

### LogBlackListedModules

Event describing blacklisting action of modules by owner.

```solidity
event LogBlackListedModules(address[] modules);
```

**Parameters**

| Name      | Type        | Description                                                               |
| --------- | ----------- | ------------------------------------------------------------------------- |
| `modules` | `address[]` | list of addresses corresponding to old modules that has been blacklisted. |

## Errors

### AddressZero

_triggered when an address that should not
be zero is equal to address zero._

```solidity
error AddressZero(string property);
```

### OnlyManager

_triggered when the caller is different than
the manager._

```solidity
error OnlyManager(address caller, address manager);
```

### CallFailed

_triggered when a low level call failed during
execution._

```solidity
error CallFailed();
```

### SameModule

_triggered when manager try to set the active
module as active._

```solidity
error SameModule();
```

### SameManager

_triggered when owner of the vault try to set the
manager with the current manager._

```solidity
error SameManager();
```

### ModuleNotEmpty

_triggered when all tokens withdrawal has been done
during a switch of module._

```solidity
error ModuleNotEmpty(uint256 amount0, uint256 amount1);
```

### AlreadyWhitelisted

_triggered when owner try to whitelist a module
that has been already whitelisted._

```solidity
error AlreadyWhitelisted(address module);
```

### NotWhitelistedModule

_triggered when owner try to blacklist a module
that has not been whitelisted._

```solidity
error NotWhitelistedModule(address module);
```

### ActiveModule

_triggered when owner try to blacklist the active module._

```solidity
error ActiveModule();
```

### Token0GtToken1

_triggered during vault creation if token0 address is greater than
token1 address._

```solidity
error Token0GtToken1();
```

### Token0EqToken1

_triggered during vault creation if token0 address is equal to
token1 address._

```solidity
error Token0EqToken1();
```

### NotWhitelistedBeacon

_triggered when whitelisting action is occuring and module's beacon
is not whitelisted on module registry._

```solidity
error NotWhitelistedBeacon();
```

### NotSameGuardian

_triggered when guardian of the whitelisting module is different than
the guardian of the registry._

```solidity
error NotSameGuardian();
```

### NotImplemented

_triggered when a function logic is not implemented._

```solidity
error NotImplemented();
```

### ArrayNotSameLength

_triggered when two arrays suppposed to have the same length, have different length._

```solidity
error ArrayNotSameLength();
```

### OnlyOwner

_triggered when function is called by someone else than the owner._

```solidity
error OnlyOwner();
```

### WithdrawNotAllowed

_triggered when setModule action try to remove funds._

```solidity
error WithdrawNotAllowed();
```

### PositionNotInitialized

_triggered when setModule function end without
initiliazePosition call._

```solidity
error PositionNotInitialized();
```

### NotPositionInitializationCall

_triggered when the first external call of setModule function
isn't InitializePosition function._

```solidity
error NotPositionInitializationCall();
```
