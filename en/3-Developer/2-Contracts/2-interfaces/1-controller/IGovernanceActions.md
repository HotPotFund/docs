Contains governance methods that can be called by governance.


## Functions
### setGovernance
```solidity
  function setGovernance(
    address account
  ) external
```
Change governance

This function can only be called by governance.

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`account` | address | New governance address

### setVerifiedToken
```solidity
  function setVerifiedToken(
    address token,
    bool isVerified
  ) external
```
Set the token to be verified for all fund, vice versa

This function can only be called by governance.

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`token` | address | Target token
|`isVerified` | bool | Verified or unverified

### setHarvestPath
```solidity
  function setHarvestPath(
    address token,
    bytes path
  ) external
```
Set the swap path for harvest

This function can only be called by governance.

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`token` | address | Target token
|`path` | bytes | Harvest path for HPT token

### setMaxSqrtSlippage
```solidity
  function setMaxSqrtSlippage(
    uint32 sqrtSlippage
  ) external
```
Set the maximum slippage when swap, the value range is 0-1e4, the calculation formula is: MaxSwapSlippage = (1 - (sqrtSlippage/1e4)^2) * 100%
If the maximum slippage is set to 0.5%, then sqrtSlippage should be set to 9974, at this time MaxSwapSlippage = (1-(9974/1e4)^2)*100% = 0.5%

This function can only be called by governance.

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`sqrtSlippage` | uint32 | Sqrt slippage value: 0-1e4

### setMaxPriceImpact
```solidity
  function setMaxPriceImpact(
    uint32 priceImpact
  ) external
```
Set the max price impact for swap

This function can only be called by governance.

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`priceImpact` | uint32 | Price impact value: 0-1e4


