Implementation of ERC20 contract representing user fund shares.


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

Mint fund share token to depositor

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`to` | address | The recipient address
|`value` | uint256 | Fund share token amount

### _burn
```solidity
  function _burn(
    address from,
    uint256 value
  ) internal
```

Burn fund share token of `from` address

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`from` | address | The target address to be burned
|`value` | uint256 | Fund share token amount

### approve
```solidity
  function approve(
    address spender,
    uint256 value
  ) external returns (bool)
```

Sets `amount` as the allowance of `spender` over the caller's tokens.
Returns a boolean value indicating whether the operation succeeded.
IMPORTANT: Beware that changing an allowance with this method brings the risk
that someone may use both the old and the new allowance by unfortunate
transaction ordering. One possible solution to mitigate this race
condition is to first reduce the spender's allowance to 0 and set the
desired value afterwards:
https://github.com/ethereum/EIPs/issues/20#issuecomment-263524729
Emits an {Approval} event.
#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`spender` | address | Spender address
|`value` | uint256 | Fund share token amount

### transfer
```solidity
  function transfer(
    address to,
    uint256 value
  ) external returns (bool)
```

Moves `amount` tokens from the caller's account to `recipient`.
Returns a boolean value indicating whether the operation succeeded.
Emits a {Transfer} event.
#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`to` | address | The recipient address
|`value` | uint256 | Fund share token amount

### transferFrom
```solidity
  function transferFrom(
    address from,
    address to,
    uint256 value
  ) external returns (bool)
```

Moves `amount` tokens from `sender` to `recipient` using the
allowance mechanism. `amount` is then deducted from the caller's
allowance.
Returns a boolean value indicating whether the operation succeeded.
Emits a {Transfer} event.
#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`from` | address | The account from which the transfer will be initiated
|`to` | address | The recipient of the transfer
|`value` | uint256 | The amount of the transfer

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`Returns`| address | true for a successful transfer, false for unsuccessful

