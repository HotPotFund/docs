Contains standard erc20 contract methods that can be called by anyone, and expanded burn function.

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
Returns token name



### symbol
```solidity
  function symbol() external returns (string)
```
Returns token symbol



### decimals
```solidity
  function decimals() external returns (uint8)
```
Returns token decimals



### burn
```solidity
  function burn(
    uint256 value
  ) external returns (bool isSuc)
```
The user burn the tokens of specified amount


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`value` | uint256 | Quantity burned

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`isSuc`| uint256 | Whether the execution is successful
### burnFrom
```solidity
  function burnFrom(
    address from,
    uint256 value
  ) external returns (bool isSuc)
```
Approved users burn other user's tokens


#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`from` | address | Burned user
|`value` | uint256 | Quantity burned

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`isSuc`| address | Whether the execution is successful

