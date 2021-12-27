Factory contract implementation


## Functions
### constructor
```solidity
  function constructor(
    address _controller, 
    address _weth9,
    address _uniV3Factory, 
    address _uniV3Router
  ) public
```

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`_controller` | address | The controller address
|`_weth9` | address | The weth9 address
|`_uniV3Router` | address | The Uniswap V3 Factory address
|`_uniV3Factory` | address | The Uniswap V3 Router address



### getFund
```solidity
  function getFund(
    address manager,
    address token,
    uint256 lockPeriod,
    uint256 baseLine,
    uint256 managerFee
  ) external returns (address fund)
```
Returns the fund address for a given manager and a token, or address 0 if it does not exist

a manager+token mapping a fund

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`manager` | address | The address of the manager who manages the fund
|`token` | address | Managed token
|`lockPeriod` | uint256 | Fund lock-up period
|`baseLine` | uint256 | Fund manager fee baseline
|`managerFee` | uint256 | Fund manager fee ratio

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`fund`| address | Fund address
### createFund
```solidity
  function createFund(
    address token,
    bytes descriptor,
    uint256 lockPeriod,
    uint256 baseLine,
    uint256 managerFee
  ) external returns (address fund)
```
Creates a fund for the given manager and token


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`token` | address | Managed token
|`descriptor` | bytes | Fund name + description
|`lockPeriod` | uint256 | Fund lock-up period
|`baseLine` | uint256 | The fund manager fee baseline. If the ROI is higher than this baseline, the user will be charged when withdrawing
|`managerFee` | uint256 | When the ROI is greater than the baseline, the fund manager’s fee ratio

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`fund`| address | Fund address

