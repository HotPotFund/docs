# 关于WETH

[WETH (Wrapped Ether)](https://cn.etherscan.com/address/0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2) 是以太坊原生代币 ETH (Ether) 的 ERC20 转换形式。

Uniswap V3 是 ERC20 代币的交易平台，它不能交易以太坊的原生代币 ETH，必须转换为 ERC20 的形式。

作为投资者，您在 Hotpot 前端看到的所有 ETH 交易，在其内部实际上都被转换成了 WETH。您无需关心它的内部机制，可以理解为二者是等价的。

作为Set经理，如果您创建了一支以 ETH 为本币的Set。投资者存入和提取时，都是使用 ETH。而Set经理收到的收益分成，则是以 WETH 形式支付。

作为Set经理，如果您要投资包含 ETH 的交易对流动池，您在Set管理页面上看到的流动池、交易路径信息都需要选择 WETH。