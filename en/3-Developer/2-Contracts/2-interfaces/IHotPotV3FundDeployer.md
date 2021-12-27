A contract that constructs a fund must implement this to pass arguments to the fund.

This is used to avoid having constructor arguments in the fund contract, which results in the init code hash
of the fund being constant allowing the CREATE2 address of the fund to be cheaply computed on-chain.

```solidity
interface IHotPotV3FundDeployer {
    function parameters()
        external
        view
        returns (
            address weth9,
            address uniV3Factory,
            address uniswapV3Router,
            address controller,
            address manager,
            address token,
            bytes memory descriptor,
            uint lockPeriod,
            uint baseLine,
            uint managerFee
        );
}
```

## Functions
### parameters
```solidity
  function parameters(
  ) external returns (
        address weth9, 
        address uniV3Factory, 
        address uniswapV3Router, 
        address controller, 
        address manager,
        address token, 
        bytes descriptor, 
        uint256 lockPeriod, 
        uint256 baseLine, 
        uint256 managerFee)
```
Get the parameters to be used in constructing the fund, set transiently during fund creation.

Called by the fund constructor to fetch the parameters of the fund

#### Return Values:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`weth9` | address | The weth9 address
|`uniV3Factory` | address | The Uniswap V3 Factory address
|`uniswapV3Router` | address | The Uniswap V3 Router address
|`controller` | address | The controller address
|`manager` | address | The manager address of this fund
|`token` | address | The fund local token address
|`descriptor` | uint256 | Bytes string descriptor, the first 32 bytes manager name + next bytes brief description
|`lockPeriod` | uint256 | lockPeriod Fund lock up period
|`baseLine` | uint256 | Baseline of fund manager fee ratio
|`managerFee` | uint256 | When the ROI is greater than the baseline, the fund manager’s fee ratio

