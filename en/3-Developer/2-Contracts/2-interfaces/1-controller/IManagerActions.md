Contains manage methods that can be called by manager.


## Functions
### setDescriptor
```solidity
  function setDescriptor(
    address fund,
    bytes _descriptor
  ) external
```
Set fund description information

This function can only be called by manager 

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
| `fund` | address | Fund address
|`_descriptor` | bytes | The fund description information

### setDepositDeadline
```solidity
  function setDepositDeadline(
    address fund,
    uint256 deadline
  ) external
```
Set countdown timestamp for fund deposit

This function can only be called by manager 

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`fund` | address | Fund address
|`deadline` | uint256 | The Countdown timestamp for fund deposit

### setPath
```solidity
  function setPath(
    address fund,
    address distToken,
    bytes path
  ) external
```
Set the token swap path

This function can only be called by manager 
When setting the path, it cannot be modified to address 0, and the token in the path must be verified whether it is trusted

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`fund` | address | Fund address
|`distToken` | address | Target token address
|`path` | bytes | A swap path that complies with uniswap v3 swap format

### init
```solidity
  function init(
    address fund,
    address token0,
    address token1,
    uint24 fee,
    int24 tickLower,
    int24 tickUpper,
    uint256 amount,
    uint256 deadline
  ) external returns (uint128 liquidity)
```
Initialize the position and allow the investment amount to be 0.

This function can only be called by manager

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`fund` | address | Fund address
|`token0` | address | The pool's token0 address
|`token1` | address | The pool's token1 address
|`fee` | uint24 | The pool's fee
|`tickLower` | int24 | The posotion's tickLower
|`tickUpper` | int24 | The posotion's tickUpper
|`amount` | uint256 | The initial investment amount is allowed to be 0, and 0 means that only positions are initialized and no substantial investment is made
|`deadline` | uint256 | A timestamp, the current blocktime must be less than or equal to this timestamp

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`liquidity`| address | Number of liquidity added
### add
```solidity
  function add(
    address fund,
    uint256 poolIndex,
    uint256 positionIndex,
    uint256 amount,
    bool collect,
    uint256 deadline
  ) external returns (uint128 liquidity)
```
Investment in designated positions, optional reinvestment fee

This function can only be called by manager 

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`fund` | address | Fund address
|`poolIndex` | uint256 | Pool index number
|`positionIndex` | uint256 | Position index number
|`amount` | uint256 | Investment amount
|`collect` | bool | Whether to collect the fees that have been incurred and reinvest
|`deadline` | uint256 | A timestamp, the current blocktime must be less than or equal to this timestamp

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`liquidity`| address | Number of liquidity added
### sub
```solidity
  function sub(
    address fund,
    uint256 poolIndex,
    uint256 positionIndex,
    uint256 proportionX128,
    uint256 deadline
  ) external returns (uint256 amount)
```
Divestment of designated positions

This function can only be called by manager 

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`fund` | address | Fund address
|`poolIndex` | uint256 | Pool index number
|`positionIndex` | uint256 | Position index number
|`proportionX128` | uint256 | The percentage of divestment, shifted to the left by 128 bits; 0 is allowed, and 0 means that only handling fees are collected
|`deadline` | uint256 | A timestamp, the current blocktime must be less than or equal to this timestamp

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`amount`| address | The amount of fund's local currency obtained from the divestment
### move
```solidity
  function move(
    address fund,
    uint256 poolIndex,
    uint256 subIndex,
    uint256 addIndex,
    uint256 proportionX128,
    uint256 deadline
  ) external returns (uint128 liquidity)
```
Move position investment

This function can only be called by manager 

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`fund` | address | Fund address
|`poolIndex` | uint256 | Pool index number
|`subIndex` | uint256 | The index number of the position to be subtracted
|`addIndex` | uint256 | The index number of the position to be added
|`proportionX128` | uint256 | Adjust the ratio, move 128 bits to the left
|`deadline` | uint256 | A timestamp, the current blocktime must be less than or equal to this timestamp

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`liquidity`| address | Number of liquidity added after completion

