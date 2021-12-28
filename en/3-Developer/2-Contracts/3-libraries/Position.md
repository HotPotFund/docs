A library for manipulating the increase, decrease and assets query of position liquidity.


## Functions
### getAmountsForAmount0
```solidity
  function getAmountsForAmount0(
    uint160 sqrtPriceX96,
    uint160 sqrtPriceL96,
    uint160 sqrtPriceU96,
    uint256 deltaX
  ) internal returns (uint256 amount0, uint256 amount1)
```
Calculate the number of t0 and t1 needed to maximize t0 to be added to the LP of the pool

Calculation formula: DeltaX0 = DeltaX0 /( SPu*(SPc-SPl) / (SPc*(SPu-SPc)) + 1)

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`sqrtPriceX96` | uint160 | Current sqrt price
|`sqrtPriceL96` | uint160 | Sqrt price of tickLower
|`sqrtPriceU96` | uint160 | Sqrt price of tickUpper
|`deltaX` | uint256 | Delta amount of token0

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`amount0`| uint160 | Amount of token0
|`amount1`| uint160 | Amount of token1
### getAmountOutMin
```solidity
  function getAmountOutMin(
    uint256 curSqrtPirceX96,
    uint256 maxPriceImpact,
    uint256 amountIn
  ) internal returns (uint256 amountOutMin)
```
Calculate the minimum swap output value


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`curSqrtPirceX96` | uint256 | Current sqrt price
|`maxPriceImpact` | uint256 | Maximum price impact
|`amountIn` | uint256 | Input quantity

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`amountOutMin`| uint256 | Minimum output quantity
### computeSwapAmounts
```solidity
  function computeSwapAmounts(
    struct Position.SwapParams params,
    mapping(address => bytes) buyPath
  ) internal returns (uint256 amount0Max, uint256 amount1Max)
```
Calculate the distribution of the two tokens in the designated position of the investment 
based on the amount of the fund's local token and the amount of collected fees.


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`params` | struct Position.SwapParams | Swap the parameters
|`buyPath` | mapping(address => bytes) | Path to purchase tokens

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`amount0Max`| uint256 | Maximum token0 amount
|`amount1Max`| uint256 | Maximum token1 amount
### addLiquidity
```solidity
  function addLiquidity(
    struct Position.Info self,
    struct Position.AddParams params,
    mapping(address => bytes) sellPath,
    mapping(address => bytes) buyPath
  ) public returns (uint128 liquidity)
```
Add LP to the specified position


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`self` | struct Position.Info | Position information
|`params` | struct Position.AddParams | Investment information
|`sellPath` | mapping(address => bytes) | Path to sell tokens
|`buyPath` | mapping(address => bytes) | Path to buy tokens

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`liquidity`| struct Position.Info | LP obtained when adding the position


### burnAndCollect
```solidity
  function burnAndCollect(
    struct Position.Info pool,
    address proportionX128
  ) public returns (uint256 amount0, uint256 amount1)
```
Brun the LP in the specified position and get back 2 tokens


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`pool` | struct Position.Info | UniswapV3Pool
|`proportionX128` | address | Burn's share of LP

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`amount0`| uint256 | Amount of token0 obtained
|`amount1`| uint256 | Amount of token1 obtained


### subLiquidity
```solidity
  function subLiquidity(
    struct Position.Info self,
    struct Position.SubParams params
  ) public returns (uint256 amount)
```
Reduce the LP of the specified position and get back the local token.


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`self` | struct Position.Info | Specified position
|`params` | struct Position.SubParams | UniswapV3 pool and quantity to be subtracted

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`amount`| uint256 | The amount of fund local token obtained


### assetsOfPool
```solidity
  function assetsOfPool(
    struct Position.Info[] self,
    address pool,
    address token,
    mapping(address => bytes) sellPath,
    address uniV3Factory
  ) public returns (uint256 amount, uint256[])
```
Obtain all assets of a certain liquidity pool (measured in the fund's local token)


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`self` | struct Position.Info[] | All posotions of the specified pool
|`pool` | address | Pool address
|`token` | address | Fund local token address
|`sellPath` | mapping(address => bytes) | Path to sell tokens
|`uniV3Factory` | address | Uniswap V3 factory address

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`amount`| uint256 | Assets of pool , amounts Amount of assets per position 


### assets
```solidity
  function assets(
    struct Position.Info self,
    address pool,
    address token,
    mapping(address => bytes) sellPath,
    address uniV3Factory
  ) public returns (uint256 amount)
```
Obtain a position, all assets measured in the fund's token


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`self` | struct Position.Info | Specified position
|`pool` | address | Pool index of the position
|`token` | address | Fund local token address
|`sellPath` | mapping(address => bytes) | Path to buy tokens
|`uniV3Factory` | address | Uniswap V3 factory address

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`amount`| uint256 | Amount of assets


### getAssetsOfSinglePosition
```solidity
  function getAssetsOfSinglePosition(
    struct Position.AssetsOfSinglePosition params
  ) internal returns (uint256 amount0, uint256 amount1)
```
Get all the assets of a position, including the handling fee not included in the tokensOwed.


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`params` | struct Position.AssetsOfSinglePosition | Position information

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`amount0`| uint256 | The amount of token0
|`amount1`| uint256 | The amount of token1


### getFeeGrowthInside
```solidity
  function getFeeGrowthInside(
    struct Position.FeeGrowthInsideParams params
  ) internal returns (uint256 feeGrowthInside0X128, uint256 feeGrowthInside1X128)
```
Retrieves fee growth data


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`params` | struct Position.FeeGrowthInsideParams | FeeGrowthInside parameter

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`feeGrowthInside0X128`| uint256 | The all-time fee growth in token0, per unit of liquidity, inside the position's tick boundaries
|`feeGrowthInside1X128`| uint256 | The all-time fee growth in token1, per unit of liquidity, inside the position's tick boundaries

