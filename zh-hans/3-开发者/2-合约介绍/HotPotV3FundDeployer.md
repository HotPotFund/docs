基金部署合约实现


## Functions
### deploy
```solidity
  function deploy(
    address controller,
    address manager,
    address token,
    address descriptor,
    address lockPeriod,
    address baseLine,
    bytes managerFee
  ) internal returns (address fund)
```

通过临时设置参数存储槽，然后使用给定参数部署基金，部署成功后后清除掉。


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`controller` | address | 控制器合约地址
|`manager` | address | 基金经理地址
|`token` | address | 基金本币地址
|`descriptor` | address | 基金描述信息，32 bytes的基金名称 + 任意长度的基金描述
|`lockPeriod` | address | 基金锁定期限
|`baseLine` | address | 基金收费基线
|`managerFee` | bytes | 当收益率大于基线时，用户的收益分成比例



#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`fund`| address | 基金合约地址

