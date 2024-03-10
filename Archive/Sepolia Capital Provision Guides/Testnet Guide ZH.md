# Morpheus Capital Providers 智能合约在以太坊Sepolia和Arbitrum Sepolia网络的测试指南


## 介绍
要参与Morpheus Capital Providers智能合约在以太坊Sepolia和Arbitrum Sepolia网络的测试，以下是主要步骤：
1) 获取SepoliaETH
2) 在以太坊Sepolia网络上获取stETH
3) 将stETH存入以太坊Sepolia网络的分发合约
4) 使用Layer Zero桥在Arbitrum Sepolia上领取MOR奖励


## 智能合约地址
以太坊Sepolia 
- 分发: [0x0Ad2fa5D8F420ff6D87192b32d89faf70466b30b](https://sepolia.etherscan.io/address/0x0Ad2fa5D8F420ff6D87192b32d89faf70466b30b#code) 
- stETH: [0x84BE06be19F956dEe06d4870CdDa76AF2e0385f5](https://sepolia.etherscan.io/address/0x84BE06be19F956dEe06d4870CdDa76AF2e0385f5#code)
  
Arbitrum Sepolia 
- MOR: [0xe6d01d086a844a61641c75f1bca572e7aa70e154](https://sepolia.arbiscan.io/address/0xe6d01d086a844a61641c75f1bca572e7aa70e154#code)


## 如何获取Sepolia ETH？
- 首先我们需要安装Metamask或其他web3钱包。我们需要进入网络设置，通常默认设置为以太坊，然后选择Sepolia测试网作为网络。
- 下一步是用SepoliaETH为您的地址充值。如果您使用的是新地址，可以使用像https://sepolia-faucet.pk910.de/# 或https://sepoliafaucet.com/ 这样的网站来获取SepoliaETH。
- 对于Sepolia测试网，还有很多其他的水龙头可以找到，但通常需要一个在主以太坊网络上活跃的地址。


## 如何获取stETH？
由于stETH测试代币没有在Sepolia网络上正式部署，我们将使用我们部署的具有核心功能的该代币副本。

我们需要访问[stETH](https://sepolia.etherscan.io/address/0x84BE06be19F956dEe06d4870CdDa76AF2e0385f5#writeContract)合约，打开“合约”标签页，然后是“写入合约”标签页。不要忘记连接您的钱包，它应该有足够的本地代币来支付燃气费。

![stETHContract](https://github.com/antonbosss/fantastic-bassoon/blob/SepoliaTestnetGuide/stETH-580x648.png)

需要选择`mint()`函数来铸造所需数量的stETH。 
作为参数：
- `account_`：代币将被记入的地址
- `amount_`：代币数量，以WEI为单位，而不是ETH。您可以使用这个单位转换计算器 https://eth-converter.com 来帮助您。例如，如果您需要0.01 stETH，那就等于10000000000000000 WEI。 

在图片中的例子里，向地址0xa4DB...2259铸造了100 stETH（以WEI表示）。

最后我们需要点击“写入”并在钱包中确认交易。


## 如何检查stETH余额？
我们需要访问[stETH](https://sepolia.etherscan.io/address/0x84BE06be19F956dEe06d4870CdDa76AF2e0385f5#readContract)合约，打开“合约”标签页，然后是“读取合约”标签页。不要忘记连接您的钱包，它应该有足够的本地代币来支付燃气费。

![stETHContract](https://github.com/antonbosss/fantastic-bassoon/blob/SepoliaTestnetGuide/check-stETH.png)

需要调用`balanceOf()`函数，并在`account_`字段中指定您的地址。结果，我们将知道钱包上有多少代币。
在图片上的例子中，地址0xa4DB...2259有1000 stETH，以WEI表示。

另一种检查方式是在您的web3钱包中添加stETH代币。对于Metamask钱包，请按照此[指南](https://support.metamask.io/hc/en-us/articles/360015489031-How-to-display-tokens-in-MetaMask#h_01FWH492CHY60HWPC28RW0872H)中的步骤操作，并填写stETH代币的合约地址`0x84BE06be19F956dEe06d4870CdDa76AF2e0385f5`


## 如何将stETH存入合约？
我们需要访问[stETH](https://sepolia.etherscan.io/address/0x84BE06be19F956dEe06d4870CdDa76AF2e0385f5#writeContract)合约，打开“合约”标签页，然后是“写入合约”标签页。不要忘记连接您的钱包，它应该有足够的本地代币来支付燃气费。

![stETHContract](https://github.com/antonbosss/fantastic-bassoon/blob/SepoliaTestnetGuide/stethapproval.png)

在贡献之前，我们需要给分发合约一个“批准”，以转移我们的stETH代币。需要选择`approve()`函数来为分发合约添加授权。作为参数：
- `spender`：分发合约地址 - `0x0Ad2fa5D8F420ff6D87192b32d89faf70466b30b`
- `amount`：代币数量，以WEI为单位。应该等于或多于存入金额。您可以使用这个单位转换计算器 https://eth-converter.com 来帮助您。

点击“写入”并确认交易。

然后，我们需要转到[分发](https://sepolia.etherscan.io/address/0x0Ad2fa5D8F420ff6D87192b32d89faf70466b30b#writeProxyContract)合约，打开“合约”标签页，然后是“写入代理”标签页。不要忘记连接您的钱包，它应该有足够的本地代币来支付燃气费。

![DistributionContract](https://github.com/antonbosss/fantastic-bassoon/blob/SepoliaTestnetGuide/stake.png)

需要选择`stake()`函数来将stETH代币存入智能合约。 
作为参数：
- `poolId_`：池标识符，只允许存在且公开的池；测试目的输入“0”；
- `amount_`：代币数量，以WEI为单位。（这个例子中是10 stETH）。

点击“写入”并确认交易。


## 我如何获取有关我已存入多少的信息？获得的奖励金额是多少？
我们需要转到[分发](https://sepolia.etherscan.io/address/0x0Ad2fa5D8F420ff6D87192b32d89faf70466b30b#readProxyContract)合约，打开“合约”标签页，然后是“读取代理”标签页。不要忘记连接您的钱包，它应该有足够的本地代币来支付燃气费。

为此我们有两个函数，第一个显示已经获得了多少奖励，奖励每秒都在增加。

![DistributionContract](https://github.com/antonbosss/fantastic-bassoon/blob/SepoliaTestnetGuide/rewards.png)

要检查奖励金额，您需要调用`getCurrentUserReward`函数，在其中需要传递群组号码和您的地址（或您想了解的用户的地址）。结果，我们将知道此刻有多少奖励。金额以WEI表示，您可以使用这个单位转换计算器 https://eth-converter.com 来帮助您。

第二个函数将显示用户投资了多少代币，参数与第一个函数调用类似。函数名为`usersData()`。

![DistributionContract](https://github.com/antonbosss/fantastic-bassoon/blob/SepoliaTestnetGuide/stakedamount.png)


## 如何从合约中提取stETH？
我们需要访问[分发](https://sepolia.etherscan.io/address/0x0Ad2fa5D8F420ff6D87192b32d89faf70466b30b#writeProxyContract)合约，打开“合约”标签页，然后是“写入代理”标签页。不要忘记连接您的钱包，它应该有足够的本地代币来支付燃气费。

![DistributionContract](https://github.com/antonbosss/fantastic-bassoon/blob/SepoliaTestnetGuide/withdraw.png)

需要选择`withdraw()`函数来提取所需数量的stETH。 
作为参数：
- `poolId_`：池标识符；测试目的输入“0”；
- `amount_`：代币数量，以WEI为单位。

点击“写入”并确认交易。


## 如何领取奖励？
我们需要访问[分发](https://sepolia.etherscan.io/address/0x0Ad2fa5D8F420ff6D87192b32d89faf70466b30b#writeProxyContract)，打开“合约”标签页，然后是“写入代理”标签页。不要忘记连接您的钱包，它应该有足够的本地代币来支付燃气费。

![DistributionContract](https://github.com/antonbosss/fantastic-bassoon/blob/SepoliaTestnetGuide/claim.png)

MOR代币的铸造发生在Arbitrum Sepolia网络上，所以我们需要一个Layer Zero桥来帮助我们完成这项工作。

用户需要做的就是调用`claim()`函数。
作为参数：
- `claim`：在这里您需要指定您将与交易一起发送的本地代币数量（以ETH为单位），该金额将用作目的网络上的铸造费用。您可以指定更多，剩余的部分将被退还给发送者。
- `poolId_`：池标识符；测试目的输入“0”；
- `user_`：将为其铸造代币的用户地址。
  
点击“写入”并确认交易。

很好，我们的奖励现在以MOR代币的形式在Arbitrum Sepolia上，您可以使用这个[指南](https://support.metamask.io/hc/en-us/articles/360015489031-How-to-display-tokens-in-MetaMask#h_01FWH492CHY60HWPC28RW0872H)将代币地址`0xe6d01d086a844a61641c75f1bca572e7aa70e154`导入到您的Metamask列表中，或者像我们对stETH代币所做的那样通过智能合约检查您的余额。


## 如何获取Arbitrum Sepolia ETH？
首先我们需要安装Metamask或其他web3钱包。然后我们需要手动添加Arbitrum Sepolia或使用[Chainlist](https://chainlist.org/?testnets=true&search=arbitrum+sepolia)并点击“添加到Metamask”

下一步是用Arbitrum Sepolia ETH为您的地址充值。您可以使用像https://faucet.quicknode.com/arbitrum/sepolia 或https://faucet.triangleplatform.com/arbitrum/sepolia 这样的水龙头来获取一些用于支付费用的代币。

**如果您对更深入的测试网指南感兴趣，请按照[链接](https://docs.google.com/document/d/1DbNx-CBpHjFUvIhbKHJSOshCKNTWlng7SeLzzn95AKY/edit)提供的指南进行操作**


