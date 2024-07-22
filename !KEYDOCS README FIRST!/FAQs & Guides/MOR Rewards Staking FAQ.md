# MOR Rewards Staking (MRS) FAQ
### Why does Morpheus need rewards staking?
The MRS has been introduced as a community initiative to close the negative feedback loop at the capital providers bucket and separate the real contributors from short-term opportunists.

### How does MOR Rewards Staking (MRS) work?
In simple terms, Morpheus contributors can stake MOR reward claims for a future date. In exchange, contributors get a "Power Factor" or just "Power" that amplifies their MOR rewards.

### How is the Power Factor determined?
The Power Factor mirrors the dilution rate due to daily emissions contributors experience while staking the MOR rewards. The equation can be found in the [MRC42](https://github.com/antonbosss/MRC/blob/main/IN%20PROGRESS/MRC42.md#the-time-power-factor-shortened-power).

### What is the maximum Power Factor multiplier?
The maximum Power Factor multiplier is 10.7x if staked for 6 years.

### For how long can I stake my rewards?
There are no limits, but Power factor starts to grow from 1x after six months of staking and reach its maximum of 10.7x if rewards are staked for six years.
While there are no limits, the reasonable range is from six months to six years.

### Can I stake MOR that I already have in my wallet?
No, only future MOR reward claims can participate in this staking.

### Who is eligible for rewards staking?
All four types of Morpheus contributions (Code, Capital, Compute, or Builders) can participate in MRS. Capital and Code will go live first, with Compute and Builder rewards staking following afterward.

### I'm a contributor, do I have to stake my rewards?
Staking rewards is not mandatory, but without it, you will not gain Power Factor.

### Can I decrease or increase the staking period?
No, the MOR staking period can only be increased.

### Can I withdraw rewards earlier?
The user is not able to withdraw their MOR rewards until the end of the MRS period.

### MRC states that every transaction will recalculate Power. I’d like to know more.
Not every transaction will trigger recalculation, but only transactions with the Distribution contract, due to the technical specifics of the contract. 
For example, depositing or withdrawing stETH for capital providers, or increasing or decreasing weights for code contributors.

### If I want to buy or sell MOR from the wallet where rewards are staked, will this trigger recalculation?
No, because these transactions do not call functions of the Distribution contract.

### Do staking rewards affect MOR emissions?
No, MRS has no impact on daily MOR emissions, but due to staking, fewer MOR tokens will flow into circulation.

### What should I do to stake my reward?
You will be able to do that via the dashboard or directly through the smart contract. If you are a code provider, you can also submit the staking time with your contribution submission.

### I'm a capital contributor. If I stake my reward, will I be able to withdraw stETH?
Nothing changes the ability of capital contributors to withdraw their stETH (beyond the normal 7 days), only the claiming of MOR rewards is delayed. However, when you withdraw stETH, you will no longer get rewards.

### I'd like to have more information about MRS.
You are welcome to read the full version of the proposal [MRC42](https://github.com/MorpheusAIs/MRC/blob/main/IN%20PROGRESS/MRC42.md).

### I have a question I didn’t find the answer to.
Please ask it in the Discord in the [#capital-providers](https://discord.com/channels/1151741790408429580/1167520881908666569) or [#code-providers](https://discord.com/channels/1151741790408429580/1167520984849469530) channel.

