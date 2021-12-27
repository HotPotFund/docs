Fund contract implementation


## Functions
### deposit
```solidity
  function deposit(
    uint256 amount
  ) external returns (uint256 share)
```
The user deposits the local token of the fund

The deposit function is suitable for ERC20 funds, if it is an ETH fund (internally converted to WETH9), it should be directly transferred to the fund contract.

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`amount` | uint256 | Deposit amount

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`share`| uint256 | Fund shares obtained by users
### _deposit
```solidity
  function _deposit(
    uint amount, 
    uint total_assets
  ) internal returns (uint256 share)
```

Store user deposit status. 

Returns fund share amount.

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`amount` | uint256 | Deposit amount
|`total_assets` | uint256 | Fund total assets


### receive
```solidity
  function receive() external payable
```

Used to receive user ETH investment


### withdraw
```solidity
  function withdraw(
    uint256 share,
    uint256 amountMin,
    uint256 deadline
  ) external returns (uint256 amount)
```
The user withdraws some local token of the specified share


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`share` | uint256 | Amount of fund shares withdrawn
|`amountMin` | uint256 | Minimum extraction value
|`deadline` | uint256 | The deadline timestamp of transaction

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`amount`| uint256 | Returns the amount of fund local token
### poolsLength
```solidity
  function poolsLength() external returns (uint256)
```
Get pool array length



### positionsLength
```solidity
  function positionsLength(
    uint256 poolIndex
  ) external returns (uint256)
```
Get the length of the position array of the pool


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`poolIndex` | uint256 | Pool index number

### setDescriptor
```solidity
  function setDescriptor(
    bytes _descriptor
  ) external
```
Set fund description information

This function can only be called by controller 

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`_descriptor` | bytes | Fund description information

### setDepositDeadline
```solidity
  function setDepositDeadline(
    uint256 deadline
  ) external
```
Set countdown timestamp for fund deposit

This function can only be called by controller 

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`deadline` | uint256 | The Countdown timestamp for fund deposit

### setPath
```solidity
  function setPath(
    address distToken,
    bytes buy,
    bytes sell
  ) external
```
Set the token swap path

To modify sellPath, you need to clear the relevant pool position assets first
#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`distToken` | address | Target token address
|`buy` | bytes | Purchase path (fundToken->distToken)
|`sell` | bytes | Sales path (distToken->fundToken)

### uniswapV3MintCallback
```solidity
  function uniswapV3MintCallback(
    uint256 amount0Owed,
    uint256 amount1Owed,
    bytes data
  ) external
```
Called to `msg.sender` after minting liquidity to a position from IUniswapV3Pool#mint.

In the implementation you must pay the pool tokens owed for the minted liquidity.
The caller of this method must be checked to be a UniswapV3Pool deployed by the canonical UniswapV3Factory.

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`amount0Owed` | uint256 | The amount of token0 due to the pool for the minted liquidity
|`amount1Owed` | uint256 | The amount of token1 due to the pool for the minted liquidity
|`data` | bytes | Any data passed through by the caller via the IUniswapV3PoolActions#mint call

### init
```solidity
  function init(
    address token0,
    address token1,
    uint24 fee,
    int24 tickLower,
    int24 tickUpper,
    uint256 amount,
    uint32 maxPIS
  ) external returns (uint128 liquidity)
```
Initialize the position and allow the investment amount to be 0.

This function can only be called by controller

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`token0` | address | The pool's token0 address
|`token1` | address | The pool's token1 address
|`fee` | uint24 | The pool's fee
|`tickLower` | int24 | The posotion's tickLower
|`tickUpper` | int24 | The posotion's tickUpper
|`amount` | uint256 | The initial investment amount is allowed to be 0, and 0 means that only positions are initialized and no substantial investment is made
|`maxPIS` | uint32 | Maximum price impact and price slippage

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`liquidity`| address | Number of liquidity added
### add
```solidity
  function add(
    uint256 poolIndex,
    uint256 positionIndex,
    uint256 amount,
    bool collect,
    uint32 maxPIS
  ) external returns (uint128 liquidity)
```
Investment in designated positions, optional reinvestment fee

This function can only be called by controller 

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`poolIndex` | uint256 | Pool index number
|`positionIndex` | uint256 | Position index number
|`amount` | uint256 | Investment amount
|`collect` | bool | Whether to collect the fees that have been incurred and reinvest
|`maxPIS` | uint32 | Maximum price impact and price slippage

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`liquidity`| uint256 | Number of liquidity added
### sub
```solidity
  function sub(
    uint256 poolIndex,
    uint256 positionIndex,
    uint256 proportionX128,
    uint32 maxPIS
  ) external returns (uint256 amount)
```
Divestment of designated positions

This function can only be called by controller 

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`poolIndex` | uint256 | Pool index number
|`positionIndex` | uint256 | Position index number
|`proportionX128` | uint256 | The percentage of divestment, shifted to the left by 128 bits; 0 is allowed, and 0 means that only handling fees are collected
|`maxPIS` | uint32 | Maximum price impact and price slippage

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`amount`| uint256 | The amount of fund's local currency obtained from the divestment
### move
```solidity
  function move(
    uint256 poolIndex,
    uint256 subIndex,
    uint256 addIndex,
    uint256 proportionX128,
    uint32 maxPIS
  ) external returns (uint128 liquidity)
```
Move position investment

This function can only be called by controller 

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`poolIndex` | uint256 | Pool index number
|`subIndex` | uint256 | The index number of the position to be subtracted
|`addIndex` | uint256 | The index number of the position to be added
|`proportionX128` | uint256 | Adjust the ratio, move 128 bits to the left
|`maxPIS` | uint32 | Maximum price impact and price slippage

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`liquidity`| uint256 | Number of liquidity added after completion
### assetsOfPosition
```solidity
  function assetsOfPosition(
    uint256 poolIndex,
    uint256 positionIndex
  ) public returns (uint256 amount)
```
Get the number of assets in the specified position


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`poolIndex` | uint256 | Pool index number
|`positionIndex` | uint256 | Position index number

### assetsOfPool
```solidity
  function assetsOfPool(
    uint256 poolIndex
  ) public returns (uint256 amount)
```
Get the amount of assets in the specified pool


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`poolIndex` | uint256 | Pool index number

### totalAssets
```solidity
  function totalAssets() public returns (uint256 amount)
```
Get total assets of fund

Amount of total assets denominated in fund local token


### _assetsOfPool
```solidity
  function _assetsOfPool(
    uint poolIndex
  ) internal returns (uint256 amount, uint256[])
```

Get assets of specified pool

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`poolIndex` | uint256 | Pool index number


