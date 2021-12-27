Deployer contract implementation


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

Deploys a fund with the given parameters by transiently setting the parameters storage slot and then
clearing it after deploying the fund.

#### Parameters:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`controller` | address | The controller address
|`manager` | address | The manager address of this fund
|`token` | address | The local token address
|`descriptor` | address | bytes string descriptor, the first 32 bytes manager name + next bytes brief description
|`lockPeriod` | address | Fund lock up period
|`baseLine` | address | Baseline of fund manager fee ratio
|`managerFee` | bytes | When the ROI is greater than the baseline, the fund manager’s fee ratio

#### Return Values:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`fund`| address | Fund address

