The HotPotFunds Factory facilitates creation of HotPotFunds funds.

```solidity
interface IHotPotV3FundFactory {
    event FundCreated(
        address indexed manager,
        address indexed token,
        address indexed fund
    );

    function WETH9() external view returns (address);

    function uniV3Factory() external view returns (address);

    function uniV3Router() external view returns (address);

    function controller() external view returns(address);

    function getFund(address manager, address token, uint lockPeriod, uint baseLine, uint managerFee) external view returns (address fund);

    function createFund(address token, bytes calldata descriptor, uint lockPeriod, uint baseLine, uint managerFee) external returns (address fund);
}
```

## Functions
### WETH9
```solidity
  function WETH9() external returns (address)
```
Returns the address of WETH9



### uniV3Factory
```solidity
  function uniV3Factory() external returns (address)
```
Returns the address of the Uniswap V3 factory



### uniV3Router
```solidity
  function uniV3Router() external returns (address)
```
Returns the address of the Uniswap V3 router



### controller
```solidity
  function controller() external returns (address)
```
Returns the fund controller address



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
## Events
### FundCreated
```solidity
  event FundCreated(
    address manager,
    address token,
    address fund
  )
```
Emitted when a fund is created


#### Parameters:
| Name                           | Type          | Description                                    |
| :----------------------------- | :------------ | :--------------------------------------------- |
|`manager`| address | The manager address of fund
|`token`| address | Deposit or withdrawal token supported by the fund
|`fund`| address | The fund is created

