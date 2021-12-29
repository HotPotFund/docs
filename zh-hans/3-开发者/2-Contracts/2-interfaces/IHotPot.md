本接口包含任何人都可以调用的标准erc20合约方法，并扩展了销毁功能。

```solidity
interface IHotPot is IERC20{
    function name() external view returns (string memory);

    function symbol() external view returns (string memory);

    function decimals() external view returns (uint8);

    function burn(uint value) external returns (bool isSuc) ;

    function burnFrom(address from, uint value) external returns (bool isSuc);
}
```

## Functions
### name
```solidity
  function name() external returns (string)
```
返回代币名称



### symbol
```solidity
  function symbol() external returns (string)
```
返回代币符号



### decimals
```solidity
  function decimals() external returns (uint8)
```
返回代币精度


### burn
```solidity
  function burn(
    uint256 value
  ) external returns (bool isSuc)
```
销毁指定数量的代币，返回销毁是否成功。

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`value` | uint256 | 销毁数量

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`isSuc`| uint256 | 是否执行成功
### burnFrom
```solidity
  function burnFrom(
    address from,
    uint256 value
  ) external returns (bool isSuc)
```
被授权者`msg.sender`销毁其它用户`from`指定数量`value`的代币


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`from` | address | 被销毁掉代币的用户地址
|`value` | uint256 | 销毁数量

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`isSuc`| address | 是否销毁成功
