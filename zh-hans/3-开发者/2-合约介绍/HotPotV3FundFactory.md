创建基金合约的工厂合约实现

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
|`_controller` | address | 控制器合约地址
|`_weth9` | address | WETH合约地址
|`_uniV3Router` | address | Uniswap V3 工厂合约地址
|`_uniV3Factory` | address | Uniswap V3 路由合约地址



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
|`fund`| address | 基金合约地址

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
|`fund`| address | 基金合约地址

