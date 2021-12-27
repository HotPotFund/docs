Contains controller state variables and read-only methods that can be called by anyone.


## Functions
### uniV3Router
```solidity
  function uniV3Router() external returns (address)
```
Returns the address of the Uniswap V3 router



### uniV3Factory
```solidity
  function uniV3Factory() external returns (address)
```
Returns the address of the Uniswap V3 facotry



### hotpot
```solidity
  function hotpot() external returns (address)
```
Returns the address of the project's governance token HPT



### governance
```solidity
  function governance() external returns (address)
```
Returns governance account address



### WETH9
```solidity
  function WETH9() external returns (address)
```
Returns the address of WETH9



### verifiedToken
```solidity
  function verifiedToken(
    address token
  ) external returns (bool)
```
Check whether the token is verified

The call will revert if the the token argument is address 0.

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`token` | address | Token address to be checked

### harvestPath
```solidity
  function harvestPath(
    address token
  ) external returns (bytes)
```
Get swap path at harvest


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`token` | address | Tokens to be exchanged

### maxSqrtSlippage
```solidity
  function maxSqrtSlippage() external returns (uint32)
```
Returns the maximum slippage when swap, the value range is 0-1e4, the calculation formula is: MaxSwapSlippage = (1-(sqrtSlippage/1e4)^2) * 100%,
If the maximum slippage is set to 0.5%, then sqrtSlippage should be set to 9974, at this time MaxSwapSlippage = (1-(9974/1e4)^2)*100% = 0.5%



### maxPriceImpact
```solidity
  function maxPriceImpact() external returns (uint32)
```
Returns the maximum price impact during swap, the value range is 0-1e4
