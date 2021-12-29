本抽象合约允许在对合约的单次调用中调用多个方法。


## Functions
### multicall
```solidity
  function multicall(
    bytes[] data
  ) external returns (bytes[] results)
```
调用当前合约中的多个函数，如果都成功则返回所有函数的数据。

对于可从multicall调用的任何方法，要注意考虑`msg.value`是否有受信任限制。

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`data` | bytes[] | 对此合约进行的多个调用的函数编码数据

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`results`| bytes[] | 用bytes data表示的每个调用的结果


