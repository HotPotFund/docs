本接口继承至标准的ERC20接口，用于实现基金份额代币。

```solidity
interface IHotPotV3FundERC20 is IERC20{
    function name() external view returns (string memory);

    function symbol() external view returns (string memory);
    
    function decimals() external view returns (uint8);
}
```

## Functions
### name
```solidity
  function name() external returns (string)
```
返回基金份额代币名称



### symbol
```solidity
  function symbol() external returns (string)
```
返回基金份额代币符号



### decimals
```solidity
  function decimals() external returns (uint8)
```
返回基金份额代币精度



