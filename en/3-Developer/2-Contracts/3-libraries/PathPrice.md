A library for calculating sqrt price of a swap path.


## Functions
### getSqrtPriceX96
```solidity
  function getSqrtPriceX96(
    bytes path
  ) internal returns (uint256 sqrtPriceX96)
```
Get the sqrtPriceX96 of the current price of the target path


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`path` | bytes | Swap path

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`sqrtPriceX96`| bytes | The sqrt price of the price (X 2^96), the price of tokenOut / tokenIn for a given swap path
### getSqrtPriceX96Last
```solidity
  function getSqrtPriceX96Last(
    bytes path
  ) internal returns (uint256 sqrtPriceX96Last)
```
Get the sqrtPriceX96Last of the current price of the target path


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`path` | bytes | Swap path

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`sqrtPriceX96Last`| bytes | The sqrt price of the lastest price (X 2^96), the price of tokenOut / tokenIn for a given swap path
### verifySlippage
```solidity
  function verifySlippage(
    bytes path,
    address uniV3Factory,
    uint32 maxSqrtSlippage
  ) internal returns (uint256)
```
Verify whether the swap slippage meets the conditions


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`path` | bytes | Swap path
|`uniV3Factory` | address | uniswap v3 factory
|`maxSqrtSlippage` | uint32 | Maximum slippage, maximum value: 1e4

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`current`| bytes | Current price

