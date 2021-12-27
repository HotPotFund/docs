构建基金的合约必须实现它以将参数传递给基金合约。

这个可以避免在构造基金合约时有构造参数，可以在用CREATE2创建基金合约地址时进行廉价计算。

```solidity
interface IHotPotV3FundDeployer {
    function parameters()
        external
        view
        returns (
            address weth9,
            address uniV3Factory,
            address uniswapV3Router,
            address controller,
            address manager,
            address token,
            bytes memory descriptor,
            uint lockPeriod,
            uint baseLine,
            uint managerFee
        );
}
```

## Functions
### parameters
```solidity
  function parameters(
  ) external returns (
        address weth9, 
        address uniV3Factory, 
        address uniswapV3Router, 
        address controller, 
        address manager,
        address token, 
        bytes descriptor, 
        uint256 lockPeriod, 
        uint256 baseLine, 
        uint256 managerFee)
```
获取用于构建基金的参数，在基金创建期间临时设置。

由基金在构成器函数中调用，以便获取到基金初始化参数。

#### Return Values:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`weth9` | address | WETH9 地址
|`uniV3Factory` | address | Uniswap V3工厂合约地址
|`uniswapV3Router` | address | Uniswap V3路由合约地址
|`controller` | address | 控制器合约地址
|`manager` | address | 基金经理地址
|`token` | address | 基金管理的基金本币地址
|`descriptor` | uint256 | 基金描述信息
|`lockPeriod` | uint256 | 基金存入锁定期
|`baseLine` | uint256 | 基金收费基线
|`managerFee` | uint256 | 当收益率大于基线时，用户的收益分成比例

