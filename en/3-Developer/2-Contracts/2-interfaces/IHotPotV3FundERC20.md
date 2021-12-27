Contains standard erc20 contract methods and state variables.

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
Return token name



### symbol
```solidity
  function symbol() external returns (string)
```
Return token symbol



### decimals
```solidity
  function decimals() external returns (uint8)
```
Return token decimals




