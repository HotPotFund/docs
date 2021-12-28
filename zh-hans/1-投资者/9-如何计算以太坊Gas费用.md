# 如何计算以太坊 Gas 费用?

以太坊上每一笔交易，都需要用 ETH 支付 Gas 费用。EIP 1559 之前，Gas 费用是支付给矿工的，所以 Gas 费又被称作**矿工费**。EIP 1559 上线之后，Gas 费的大部分被销毁，但矿工费这个名称依然沿用了下来。

为了在以太坊上完成操作，您的钱包中必须持有一定数量的 ETH，用于支付 Gas。每笔交易所需 Gas 费用的计算公式是：

$$Gas\ Used\ *\ Gas\ Price$$​​

## Gas 单价(Gas Price)

Gas 单价即1个 Gas 单位的价格。

Hotpot Dapp 上提供了当前的 Gas 单价 (以 GWei 为单位)，用该单价乘以一笔交易的 Gas 消耗量，就是需要花费的 Gas 费，Gas 费都是以 ETH 计价并支付。

以太坊每个区块有 Gas 消耗总量的上限，其上的交易是由矿工进行打包并排列交易顺序。因此，矿工从自身利益出发，会优先选择 Gas 单价高的交易进行打包。如果 Gas 单价设置过低，矿工会优先选择 Gas 高的交易打包，您的交易就会延迟。矿工会等到交易队列中您设置的 Gas 单价排位靠前的时候，再打包您的交易。如果您设置的Gas 单价很高，完成一笔交易的成本就会很高。

所以，建议不要在链上交易拥堵，Gas 单价很高的时候进行交易。

您可以在钱包软件中自行设置 Gas 单价，但如果您设置的 Gas 单价过低，一则可能会等待很长时间都不能完成交易；二则可能由于时间超出了您在 Hotpot 交易设置中设置的交易截止时间，即便交易得以执行也会失败。 

除了 Hotpot 提供的当前 Gas 单价之外，您还可以在 [etherscan](https://cn.etherscan.com/gastracker#historicaldata) 查询历史 Gas 单价。类似的 Gas 查询网址很多，这里不一一列举。

## Gas 消耗量(Gas Used)

Gas 消耗量是每笔交易所开销的 Gas 数量。

在发起一笔交易时，钱包软件会预估一个 Gas 消耗量，称作 Gas Limit，即该笔交易的 Gas 上限。在提交您的交易时，您需要确保钱包中的 ETH 数量大于 Gas Limit * Gas 单价，否则钱包软件会提示您 ETH 余额不足。

钱包软件的估算值一般会高于该笔交易实际的开销，您实际支出的 Gas 费用一般来说会低于该值。

Gas 消耗量跟交易的复杂程度有关：一笔转账 ETH 的交易，开销是 21,000 Gas 单位；一笔 ERC20 代币的转账，开销大约是4万多 Gas 单位；而一笔复杂的交易，例如部署一个复杂的智能合约，开销可能是几百万 Gas 单位。

在 Hotpot 上，一笔存入交易，Gas 消耗量从几万到10几万不等；一笔提取交易，Gas 消耗量大约是20-60万。实际的 Gas 消耗量跟基金投资的情况有关。

> 我们以一笔 Gas 单价 50 GWei，Gas 消耗量 50 万的提取交易为例，所需花费的 Gas 费用为：
>
> $$50 GWei * 500,000 = 2.5 * 10^{7} GWei$$
>
> $$1 ETH = 10^{9}GWei$$
>
> $$ 2.5 * 10^{7} / 10^{9} = 0.025 ETH$$
>
> 所开销的 Gas 费用为：0.025 ETH

Gas 费用与交易金额无关，无论您是完成一笔价值 \$1万，或者价值 \$100万的交易，Gas 费只跟 Gas 单价和该笔交易消耗的 Gas 量有关。

 ## 以太币单位

以太币 (Ether, 简写 ETH) 的最小度量单位是 Wei, 1 ETH = $$10^{18}$$ Wei

除了最小度量单位 Wei，以太币还有一些度量单位，它们的关系如下：

* **Kwei(Babbage) =** ![[公式]](https://www.zhihu.com/equation?tex=10%5E%7B3%7D) **Wei**
* **Mwei(Lovelace) =** ![[公式]](https://www.zhihu.com/equation?tex=10%5E%7B6%7D) **Wei**
* **Gwei(Shannon) =** ![[公式]](https://www.zhihu.com/equation?tex=10%5E%7B9%7D) **Wei**
* **Microether(Szabo) =** ![[公式]](https://www.zhihu.com/equation?tex=10%5E%7B12%7D) **Wei**
* **Milliether(Finney) =** ![[公式]](https://www.zhihu.com/equation?tex=10%5E%7B15%7D) **Wei**
* **Ether =** ![[公式]](https://www.zhihu.com/equation?tex=10%5E%7B18%7D) **Wei**

