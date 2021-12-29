本接口是继承至其它多个接口的接口合约。

```solidity
interface IHotPotV3Fund is 
    IHotPotV3FundERC20, 
    IHotPotV3FundEvents, 
    IHotPotV3FundState, 
    IHotPotV3FundUserActions, 
    IHotPotV3FundManagerActions
{}
```

