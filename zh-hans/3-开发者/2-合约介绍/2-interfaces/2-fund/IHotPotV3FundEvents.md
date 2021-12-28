本接口包含可以由基金合约生成的事件。

## Events
### Deposit
```solidity
  event Deposit(
    address owner,
    uint256 amount,
    uint256 share
  )
```
用户存入基金本币时触发该本事件。


#### Parameters:
| Name                           | Type          | Description                                    |
| :----------------------------- | :------------ | :--------------------------------------------- |
|`owner`| address | 存入者地址
|`amount`| uint256 | 存入数量
|`share`| uint256 | 获得的基金份额代币数量
### Withdraw
```solidity
  event Withdraw(
    address owner,
    uint256 amount,
    uint256 share
  )
```
当用户发起提取时触发本事件


#### Parameters:
| Name                           | Type          | Description                                    |
| :----------------------------- | :------------ | :--------------------------------------------- |
|`owner`| address | 提取者地址
|`amount`| uint256 | 提取金额
|`share`| uint256 | 销毁的基金份额代币数量
### SetDescriptor
```solidity
  event SetDescriptor(
    bytes descriptor
  )
```
当设置基金描述信息人触发本事件


#### Parameters:
| Name                           | Type          | Description                                    |
| :----------------------------- | :------------ | :--------------------------------------------- |
|`descriptor`| bytes | 基金描述信息
### SetDeadline
```solidity
  event SetDeadline(
    uint256 deadline
  )
```
当设置基金存入截止时间戳时触发本事件


#### Parameters:
| Name                           | Type          | Description                                    |
| :----------------------------- | :------------ | :--------------------------------------------- |
|`deadline`| uint256 | 基金存入截止时间
### SetPath
```solidity
  event SetPath(
    address distToken,
    bytes path
  )
```
当设置基金持有的代币交易路径时触发本事件


#### Parameters:
| Name                           | Type          | Description                                    |
| :----------------------------- | :------------ | :--------------------------------------------- |
|`distToken`| address | 目标地址
|`path`| bytes | 交易路径
### Init
```solidity
  event Init(
    uint256 poolIndex,
    uint256 positionIndex,
    uint256 amount
  )
```
当初始化基金头寸时触发本事件


#### Parameters:
| Name                           | Type          | Description                                    |
| :----------------------------- | :------------ | :--------------------------------------------- |
|`poolIndex`| uint256 | 池子索引位置
|`positionIndex`| uint256 | 头寸索引位置
|`amount`| uint256 | 初始投资数量
### Add
```solidity
  event Add(
    uint256 poolIndex,
    uint256 positionIndex,
    uint256 amount,
    bool collect
  )
```
当追加头寸的投资时触发本事件


#### Parameters:
| Name                           | Type          | Description                                    |
| :----------------------------- | :------------ | :--------------------------------------------- |
|`poolIndex`| uint256 | 池子索引位置
|`positionIndex`| uint256 | 头寸索引位置
|`amount`| uint256 | 初始投资数量
|`collect`| bool | 是否复投
### Sub
```solidity
  event Sub(
    uint256 poolIndex,
    uint256 positionIndex,
    uint256 proportionX128
  )
```
当撤资指定头寸时触发本事件


#### Parameters:
| Name                           | Type          | Description                                    |
| :----------------------------- | :------------ | :--------------------------------------------- |
|`poolIndex`| uint256 | 池子索引位置
|`positionIndex`| uint256 | 头寸索引位置
|`proportionX128`| uint256 | 撤资百分比，左移 128 位； 0是允许的，0表示只收取手续费
### Move
```solidity
  event Move(
    uint256 poolIndex,
    uint256 subIndex,
    uint256 addIndex,
    uint256 proportionX128
  )
```
当调整两个头寸的资金时触发本事件


#### Parameters:
| Name                           | Type          | Description                                    |
| :----------------------------- | :------------ | :--------------------------------------------- |
|`poolIndex`| uint256 | 池子索引位置
|`subIndex`| uint256 | 要撤资的头寸索引位置
|`addIndex`| uint256 | 要增资的头寸索引位置
|`proportionX128`| uint256 | 调整比例，左移128位

