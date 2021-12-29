用于计算二维数组最大值的库。


## Functions
### max
```solidity
  function max(
    uint256[][] self
  ) internal returns (uint256 index1, uint256 index2, uint256 value)
```
取二维数组中的最大值和索引


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`self` | uint256[][] | 二维数组

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`index1`| uint256 | 一维数组索引位置
|`index2`| uint256 | 二维数组索引位置
|`value`| uint256 | 最大值

