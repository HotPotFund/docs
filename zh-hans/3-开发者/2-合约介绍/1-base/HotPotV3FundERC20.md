本合约通过一个标准的ERC20合约来实现和管理用户在基金中所占份额。


## Functions
### constructor
```solidity
  function constructor() internal
```




### _mint
```solidity
  function _mint(
    address to,
    uint256 value
  ) internal
```

铸币`value`数量的基金份额代币给`to`地址

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`to` | address | 接收者地址
|`value` | uint256 | 基金份额代币数量

### _burn
```solidity
  function _burn(
    address from,
    uint256 value
  ) internal
```

销毁`from`用户`value`数量的基金份额代币

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`from` | address | 要被销毁的目标地址
|`value` | uint256 | 基金份额代币数量

### approve
```solidity
  function approve(
    address spender,
    uint256 value
  ) external returns (bool)
```

`msg.sender`授权`spender`可以转账自己的`value`数量的代币

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`spender` | address | 被授权转账的地址
|`value` | uint256 | 基金份额代币数量

### transfer
```solidity
  function transfer(
    address to,
    uint256 value
  ) external returns (bool)
```

`msg.sender`转账给`to`地址`value`数量的代币

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`to` | address | 接收者地址
|`value` | uint256 | 基金份额代币数量

### transferFrom
```solidity
  function transferFrom(
    address from,
    address to,
    uint256 value
  ) external returns (bool)
```

被授权者`msg.sender`转账`from`地址的`value`数量代币给`to`地址

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`from` | address | 扣款地址
|`to` | address | 收款地址
|`value` | uint256 | 转账数量

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`Returns`| address | true：操作成功, false：操作失败

