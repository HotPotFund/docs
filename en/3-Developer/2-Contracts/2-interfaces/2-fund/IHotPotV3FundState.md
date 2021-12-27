Contains state variables and read-only methods that can be called by anyone.


## Functions
### controller
```solidity
  function controller() external returns (address)
```
Returns controller contract address



### manager
```solidity
  function manager() external returns (address)
```
Returns fund manager address



### token
```solidity
  function token() external returns (address)
```
Returns fund local token address



### descriptor
```solidity
  function descriptor() external returns (bytes)
```
Returns 32 bytes fund name + brief description of any length



### lockPeriod
```solidity
  function lockPeriod() external returns (uint256)
```
Returns fund lock-up period



### baseLine
```solidity
  function baseLine() external returns (uint256)
```
Returns fund manager fee baseline



### managerFee
```solidity
  function managerFee() external returns (uint256)
```
Returns fund manager fee ratio



### depositDeadline
```solidity
  function depositDeadline() external returns (uint256)
```
Returns the Countdown timestamp for fund deposit



### lastDepositTime
```solidity
  function lastDepositTime(
    address account
  ) external returns (uint256)
```
Get the latest deposit time


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`account` | address | Target address

### totalInvestment
```solidity
  function totalInvestment() external returns (uint256)
```
Returns total investment



### investmentOf
```solidity
  function investmentOf(
    address owner
  ) external returns (uint256)
```
Get owner's investment


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`owner` | address | User address

### assetsOfPosition
```solidity
  function assetsOfPosition(
    uint256 poolIndex,
    uint256 positionIndex
  ) external returns (uint256)
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
  ) external returns (uint256)
```
Get the amount of assets in the specified pool


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`poolIndex` | uint256 | Pool index number

### totalAssets
```solidity
  function totalAssets() external returns (uint256)
```
Get total assets of fund

Amount of total assets denominated in fund local token


### buyPath
```solidity
  function buyPath(
    address _token
  ) external returns (bytes)
```
The purchase path from the fund's local token to the target token

Purchasing path of target tokens conforming to uniswap v3 format.

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`_token` | address | Target token address

### sellPath
```solidity
  function sellPath(
    address _token
  ) external returns (bytes)
```
The selling path from the target token to the fund's local token

Selling path of target tokens conforming to uniswap v3 format

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`_token` | address | Target token address

### pools
```solidity
  function pools(
    uint256 index
  ) external returns (address)
```
Get pool address


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`index` | uint256 | Pool index number

### positions
```solidity
  function positions(
    uint256 poolIndex,
    uint256 positionIndex
  ) external returns (bool isEmpty, int24 tickLower, int24 tickUpper)
```
Get position information

Since the fund needs to traverse the positions, a two-dimensional dynamic array is used to store the positions.

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`poolIndex` | uint256 | Pool index number
|`positionIndex` | uint256 | Position index number

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`isEmpty`| bool | Is it a empty position
|`tickLower`| uint256 | tickLower Tick lower
|`tickUpper`| uint256 | tickUpper Tick upper
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


