本接口是用户创建基金合约的构成器合约接口

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
返回WETH9地址


### uniV3Factory
```solidity
  function uniV3Factory() external returns (address)
```
返回Uniswap V3 工厂合约地址



### uniV3Router
```solidity
  function uniV3Router() external returns (address)
```
返回Uniswap V3 路由合约地址



### controller
```solidity
  function controller() external returns (address)
```
返回控制器合约地址



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
返回给定参数的基金合约地址


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`manager` | address | 基金经理地址
|`token` | address | 基金本币
|`lockPeriod` | uint256 | 基金存入锁定时间
|`baseLine` | uint256 | 基金收费基线
|`managerFee` | uint256 | 基金经理分成比例

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`fund`| address | 基金地址

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
创建一个指定参数的基金合约

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`token` | address | 基金本币地址
|`descriptor` | bytes | 基金描述信息
|`lockPeriod` | uint256 | 基金存入锁定期
|`baseLine` | uint256 | 基金收费基线
|`managerFee` | uint256 | 当收益大于基线时，基金经理的分成比例

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`fund`| address | 基金地址
## Events
### FundCreated
```solidity
  event FundCreated(
    address manager,
    address token,
    address fund
  )
```
基金合约创建成功后触发该事件


#### Parameters:
| Name                           | Type          | Description                                    |
| :----------------------------- | :------------ | :--------------------------------------------- |
|`manager`| address | 基金经理地址
|`token`| address | 基金本币地址
|`fund`| address | 基金合约地址

