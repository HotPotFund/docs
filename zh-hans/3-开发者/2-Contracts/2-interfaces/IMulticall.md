本接口定义了将合约的多次调用封装成单次调用的方法。


```solidity
interface IMulticall {
    function multicall(bytes[] calldata data) external payable returns (bytes[] memory results);
}
```

## Functions
### multicall
```solidity
  function multicall(
    bytes[] data
  ) external returns (bytes[] results)
```
在单次合约调用中，调用多个合约方法。

对于可从multicall调用的任何方法，要注意考虑`msg.value`是否有受信任限制。


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`data` | bytes[] | 包含多个调用方法的calldata数据

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`results`| bytes[] | 多个方法执行后返回的结果数据


