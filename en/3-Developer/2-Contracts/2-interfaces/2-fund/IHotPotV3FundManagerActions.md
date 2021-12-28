Contains manage methods that can be called by controller.


## Functions
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

This function can only be called by controller 
When setting the path, it cannot be modified to address 0, and the token in the path must be verified whether it is trusted

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`distToken` | address | Target token address
|`buy` | bytes | Purchase path (fundToken->distToken)
|`sell` | bytes | Sales path (distToken->fundToken)

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

