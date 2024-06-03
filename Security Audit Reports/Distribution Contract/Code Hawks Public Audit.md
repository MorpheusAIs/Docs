# MorpheusAI - Findings Report
Link to Report: https://www.codehawks.com/report/clrzgrole0007xtsq0gfdw8if

# Table of contents
- ### [Contest Summary](#contest-summary)
- ### [Results Summary](#results-summary)
- ## High Risk Findings
    - [H-01. All claimed rewards will be lost for the users using the account abstraction wallet](#H-01)
- ## Medium Risk Findings
    - [M-01. Due to no access control on `DistributionV2::_authorizeUpgrade()` anyone can change the implementation contract and can destroy the main Proxy contract.](#M-01)
- ## Low Risk Findings
    - [L-01. Any User can mint any amount of WStETH in the WStETHMock.sol and StETHMock.sol](#L-01)
    - [L-02. Use custom gas in `sendMintMessage` instead of default gas](#L-02)
    - [L-03. Create Pool in Mock Distribution is missing validations; allowing duplicates, wrong decreaseInterval value and payoutStart value](#L-03)
    - [L-04. The `editPool()` lacks a sanity check on the `payoutStart` parameter leading to incorrect or unfair reward distributions](#L-04)
    - [L-05. Do not hardcode `_zroPaymentAddress` field to `address(0)`](#L-05)
    - [L-06. LayerZeroEndpoint.send() in L1Sender.sol may revert if the user does not provide enough native gas as specified](#L-06)
    - [L-07. Users are unable to withdraw immediately, even if they stake after reaching maxEndTime](#L-07)
    - [L-08. L1Sender does not implement `supportsInterface` function](#L-08)
    - [L-09. 8 lows for mocks](#L-09)
    - [L-10. 8 lows for mocks](#L-10)


# <a id='contest-summary'></a>Contest Summary

### Sponsor: MorpheusAI

### Dates: Jan 30th, 2024 - Feb 3rd, 2024

[See more contest details here](https://www.codehawks.com/contests/clrzgrole0007xtsq0gfdw8if)

# <a id='results-summary'></a>Results Summary

### Number of findings:
   - High: 1
   - Medium: 1
   - Low: 10


# High Risk Findings

## <a id='H-01'></a>H-01. All claimed rewards will be lost for the users using the account abstraction wallet

_Submitted by [iamandreiski](/profile/clqp2o8oi0003a6nvckl3gop2), [nmirchev8](/profile/clkao1p090000ld08dv6v2xus), [0xhals](/profile/clkfub7qh0002l508bt5xdugv), [turvyfuzz](/profile/clkghm50k0008l70869gpsyyw), [SovaSlava](/profile/clml6nvdo0000js08a1137stt), [MrPotatoMagic](/profile/clk3to00g001cl5087hsgvbey), [0xG0P1](/profile/cll7r9b6y0000ia080v4wpg6l), [DenTonylifer](/profile/clocyn92t0003mf088apzq7fo). Selected submission by: [turvyfuzz](/profile/clkghm50k0008l70869gpsyyw)._      
				
### Relevant GitHub Links
	
https://github.com/Cyfrin/2024-01-Morpheus/blob/main/contracts/Distribution.sol#L174

https://github.com/Cyfrin/2024-01-Morpheus/blob/main/contracts/L1Sender.sol#L128

## Summary
Users with account abstraction wallets have different addresses across different chains for the same account, so if all rewards are claimed for someone using an account abstraction wallet, the rewards will be minted to the wrong address and lost permanently. Also, a malicious attacker/attackers who notices this could perform griefing attacks on all account abstraction wallet users by voluntarily executing `claim()` for all these users.

## Vulnerability Details
With 5.7 million users and 79 billion assets, there is a very high risk that the claim rewards will be called on safe wallet users and lose all the rewards.

Now, look at the codebase and understand how all the rewards will be lost for the users.

In the `Distribution.sol::claim()` we call the l1sender to send the mint rewards message as follows:
```solidity
L1Sender(l1Sender).sendMintMessage{value: msg.value}(user_, pendingRewards_, _msgSender());
```
Here, we can see the function passes the exact address of the user: `user_` as the receiving address on the other chain, assuming that the user has the same address across all the EVM chains; which is not the case if the user is using the account abstraction wallet.

Then, on the l1Sender contract it calls the function `sendMintMessage()` receiving the `user_` as the payload, which then calls the LayerZeroEndpoint `send` function passing the payload to LayerZeroEndpoint.
```solidity
        bytes memory payload_ = abi.encode(user_, amount_);

        ILayerZeroEndpoint(config.gateway).send{value: msg.value}(
            config.receiverChainId, // communicator LayerZero chainId
            receiverAndSenderAddresses_, // send to this address to the communicator
            payload_, // bytes payload
            payable(refundTo_), // refund address
            address(0x0), // future parameter
            bytes("") // adapterParams (see "Advanced Features")
        );
```
Then, on the l2, `lzReceive` function will be triggered, which will in turn call `_nonblockingLzReceive()` passing in the payload. The rewards will be minted to the l1 chain's account abstraction wallet address, but on l2 chain, the same person will not be the owner of that address; hence, all rewards are permanently lost. Also, a malicious attacker/attackers who notices this could perform griefing attacks on all account abstraction wallet users by voluntarily executing `claim()` for all these users.
```solidity
function _nonblockingLzReceive(
        uint16 senderChainId_,
        bytes memory senderAndReceiverAddresses_,
        bytes memory payload_
    ) private {
        require(senderChainId_ == config.senderChainId, "L2MR: invalid sender chain ID");

        address sender_;
        assembly {
            sender_ := mload(add(senderAndReceiverAddresses_, 20))
        }
        require(sender_ == config.sender, "L2MR: invalid sender address");

        (address user_, uint256 amount_) = abi.decode(payload_, (address, uint256));

        IMOR(rewardToken).mint(user_, amount_);
    }
```
## Impact
If all rewards are claimed for someone using an account abstraction wallet, the rewards will be minted to the wrong address and lost permanently.

## Recommendations
Give the user the option to pass in the address the rewards should be minted to on the l2 by adding an extra address variable to the userdata struct which should be set only by the user. 
```diff
   struct UserData {
        uint128 lastStake;
        uint256 deposited;
        uint256 rate;
        uint256 pendingRewards;
+      address l2recipient;
    }
```
Pass in the warning for account abstraction wallet holders to not to pass the same wallet.

# Medium Risk Findings

## <a id='M-01'></a>M-01. Due to no access control on `DistributionV2::_authorizeUpgrade()` anyone can change the implementation contract and can destroy the main Proxy contract.

_Submitted by [matej](/profile/clqf9x2s3000r83pidasj858e), [SovaSlava](/profile/clml6nvdo0000js08a1137stt), [0x11singh99](/profile/clkhsr7bn0000l608c9vc7ugr), [PratRed](/profile/clkkqoyem0008jw08qno0zb4f), [Denzi](/profile/clnvfit56000bl008kg599zbt), [xiao](/profile/clqmjjket0000c5aly8byzk38). Selected submission by: [0x11singh99](/profile/clkhsr7bn0000l608c9vc7ugr)._      
				
### Relevant GitHub Links
	
https://github.com/Cyfrin/2024-01-Morpheus/blob/main/contracts/mock/DistributionV2.sol#L36

https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/proxy/utils/UUPSUpgradeable.sol#L86-L90


## Vulnerability Details :

`DistributionV2` contract inheriting `UUPSUpgradeable` so overriding `_authorizeUpgrade()` function. But adding no access control to this function can lead to setting implementation contract by anyone since this function is called for authorization in `UUPSUpgradeable`. By setting any malicious contract as implementation attacker can **selfdestruct()** the proxy contract. Since implementation is called using delegatecall from proxy.

### Code Snippet :

[contracts/mock/DistributionV2.sol](https://github.com/Cyfrin/2024-01-Morpheus/blob/main/contracts/mock/DistributionV2.sol#L36)

```solidity
36:  function _authorizeUpgrade(address) internal view override {}
```

Since `DistributionV2` contract is inheriting `UUPSUpgradeable` from openzeppelin we can see in upgrading implementation address `_authorizeUpgrade()` is called.

https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/proxy/utils/UUPSUpgradeable.sol#L86C5-L90C1

```solidity
function upgradeToAndCall(address newImplementation, bytes memory data) public payable virtual onlyProxy {
        _authorizeUpgrade(newImplementation);
        _upgradeToAndCallUUPS(newImplementation, data);
    }
```

### Malicious `DistributionV2` implementation contract

```javascript
contract DistributionV2 is UUPSUpgradeable {
    IDistribution.Pool[] public pools;

    function version() external pure returns (uint256) {
        return 2;
    }

    function createPool(IDistribution.Pool calldata pool_) public {
        selfdestruct(address(0));//@audit this code will be implanted here
    }

    function getPeriodReward(uint256 poolId_, uint128 startTime_, uint128 endTime_) public view returns (uint256) {
        IDistribution.Pool storage pool = pools[poolId_];

        return LinearDistributionIntervalDecrease.getPeriodReward(
            pool.initialReward, pool.rewardDecrease, pool.payoutStart,  pool.decreaseInterval, startTime_, endTime_
        );
    }

    function _authorizeUpgrade(address) internal view override {}
}

```

First attacker will call `upgradeToAndCall` to main proxy contract which will change the implementation contract address to his malicious `DistributionV2` contract.
Now Attacker will call `createPool` to main proxy contract of `DistributionV2` and by `delegatecall` proxy will call implementation contract .It will destroy the main proxy contract using `selfdestruct()`. And erase all the storage from main proxy contract of DistributionV2.

## Impact :

The main proxy contract will be destroyed and erase all the storage from main proxy contract of DistributionV2.

## Tools Used

Manual Review

## Recommended Mitigation Steps :

Add proper access control to `_authorizeUpgrade()` function since it is used for authorization at the time of changing implementation contract address. This can be mitigated by using 'OwnableUpgradeable' of openzeppelin and add `onlyOwner` modifier to the `_authorizeUpgrade()` function so. Only owner can be authorized to upgrade the implementation address. Add one initializer function also to initialize the owner.

```diff

File : contracts/mock/DistributionV2.sol
  ...

+  import {OwnableUpgradeable} from "@openzeppelin/contracts-upgradeable/access/OwnableUpgradeable.sol";

-  contract DistributionV2 is UUPSUpgradeable {
+  contract DistributionV2 is OwnableUpgradeable, UUPSUpgradeable {

 ...


+  function Distribution_init() external initializer
+    {
+        __Ownable_init();
+        __UUPSUpgradeable_init();
+    }

       ...

- function _authorizeUpgrade(address) internal view override {}
+ function _authorizeUpgrade(address) internal view override onlyOwner {}
}

```


# Low Risk Findings

## <a id='L-01'></a>L-01. Any User can mint any amount of WStETH in the WStETHMock.sol and StETHMock.sol

_Submitted by [ubl4nk](/profile/clmknelt80000la08ioq96nnv), [Tigerfrake](/profile/clqqa49xg0006sjy9t2ly5s3p), [Pelz](/profile/clokuwofs000yih08n1oqrf6d), [matej](/profile/clqf9x2s3000r83pidasj858e), [0xWallSecurity](/profile/clqyonbnu000311viljnrqp2s), [Auditism](/profile/clk3t8gh1000iib08z1nz6equ), [Bube](/profile/clk3y8e9u000cjq08uw5phym7), [oualidpro](/profile/clkn61ppo0008l6086a909pio), [SkyHunter](/profile/clpkiuuiy0007gxi1iyf5wzzz), [King](/profile/clk4dhb4a0000k308nu6ydtgb), [greatlake](/profile/clqqqx4vv00008fmhava6pyaf), [kodyvim](/profile/clk9ly60q0004ml084a049be7), [0x11singh99](/profile/clkhsr7bn0000l608c9vc7ugr), [97Sabit](/profile/clk42eeq0007mla08lc11yszp), [0xepley](/team/clkjtgvih0001jt088aqegxjj), [PratRed](/profile/clkkqoyem0008jw08qno0zb4f), [mgf15](/profile/clk993ol40000mr08qghps3lm), [Denzi](/profile/clnvfit56000bl008kg599zbt), [smbv1923](/profile/clkp51djq001amy08d2e1slqf). Selected submission by: [Denzi](/profile/clnvfit56000bl008kg599zbt)._      
				
### Relevant GitHub Links
	
https://github.com/Cyfrin/2024-01-Morpheus/blob/main/contracts/mock/tokens/StETHMock.sol#L19-L27

https://github.com/Cyfrin/2024-01-Morpheus/blob/main/contracts/mock/tokens/WStETHMock.sol#L15-L17

## Summary

Any user can pass in an address and an amount of their choice which will then mint the specified amount of WStETH/StETHMock to the specified address.

https://github.com/Cyfrin/2024-01-Morpheus/blob/main/contracts/mock/tokens/StETHMock.sol#L19-L27

https://github.com/Cyfrin/2024-01-Morpheus/blob/main/contracts/mock/tokens/WStETHMock.sol#L15-L17

## Vulnerability Details

The issue comes from the following blocks of code in two different contracts

##### WStETHMock.sol

```solidity
function mint(address account_, uint256 amount_) external {
        _mint(account_, amount_);
    }
```

##### StETHMock.sol

```solidity
function mint(address _account, uint256 _amount) external {
        // q - missing access modifier
        require(_amount <= 1000 * (10 ** decimals()), "StETHMock: amount is too big");

        uint256 sharesAmount = getSharesByPooledEth(_amount);

        _mintShares(_account, sharesAmount);

        totalPooledEther += _amount;
    }
```

Due to missing onlyOwner modifier, anyone can call the `mint` function and mint any amount of WStETH/StETHMock to any address.

## Impact

Users can mint themselves unlimited tokens to the passed in address parameter.

#### Proof of Concept:

Consider setting up a test. User can pass in their own or any address with any amount and they will be minted that amount of tokens.

```solidity
function testAnyoneCanMint() public {
        vm.prank(user);
        stETHMock.mint(user, 1000e18);
        vm.stopPrank();

        assertEq(stETHMock.balanceOf(address(user)), 1000e18);
    }
```

```solidity
function testWStETHMockMint() public {
        vm.prank(user);
        wstETHMock.mint(user, 10e18);
        vm.stopPrank();

        console.log("Balance of user: ", wstETHMock.balanceOf(user));
    }
```


## Tools Used

Manual Review, Unit Tests

## Recommendations

Consider adding an onlyOwner access modifier so only the owner can mint the tokens for the account provided.

##### WStETHMock.sol

```diff
-function mint(address account_, uint256 amount_) external {
+function mint(address account_, uint256 amount_) external onlyOwner {
        _mint(account_, amount_);
    }
```

##### StETHMock.sol

```diff
-function mint(address _account, uint256 _amount) external {
+function mint(address _account, uint256 _amount) external onlyOwner {
        require(_amount <= 1000 * (10 ** decimals()), "StETHMock: amount is too big");

        uint256 sharesAmount = getSharesByPooledEth(_amount);

        _mintShares(_account, sharesAmount);

        totalPooledEther += _amount;
    }
```
## <a id='L-02'></a>L-02. Use custom gas in `sendMintMessage` instead of default gas

_Submitted by [abhishekthakur](/profile/clkaqh5590000k108p39ktfwl), [0xTheBlackPanther](/profile/clnca1ftl0000lf08bfytq099), [oualidpro](/profile/clkn61ppo0008l6086a909pio), [MrPotatoMagic](/profile/clk3to00g001cl5087hsgvbey), [Joshuajee](/profile/clp8tjvhb0000r61pfr2owzuy), [kaysoft](/profile/clkig5ndy001cmh08vf2kbcem), [0xsandy](/profile/clk43kus5009imb0830ko7dxy). Selected submission by: [0xTheBlackPanther](/profile/clnca1ftl0000lf08bfytq099)._      
				
### Relevant GitHub Links
	
https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/Distribution.sol#L174

https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/L1Sender.sol#L136


## **Summary:**
A potential issue related to the handling of gas limits in the `sendMintMessage` function of the `L1Sender.sol` contract was found. Currently it utilizes a default gas limit of 200,000, potentially leading to suboptimal gas usage. To address this issue, it is recommended to implement the use of `adapterParams` to allow users to set a custom gas limit, providing more flexibility and cost optimization.

## **Vulnerability Details:**
The vulnerability lies in the `sendMintMessage` function of the `L1Sender.sol`, where a default gas limit of `200,000` will be used by default. This fixed gas limit may not be optimal for all transactions, potentially leading to either overpayment for unused gas or insufficient gas for complex transactions. By not allowing users to customize the gas limit, the contract misses an opportunity for gas optimization.

## **Impact:**
The impact of the current implementation is primarily related to potential suboptimal gas usage. In scenarios where transactions have varying gas requirements, users may incur unnecessary costs or face delays due to inadequate gas limits. The issue does not pose a direct security threat but affects the efficiency and cost-effectiveness of protocol transactions.

## **Tools Used:**
Manual review.

## **Recommendations:**

**Implement `adapterParams` for Custom Gas Limit:**
   - Introduce a parameter for `adapterParams` in the `sendMintMessage` function to allow users to set a custom gas limit.
   - Ensure proper encoding and decoding of `adapterParams` according to the LayerZero documentation.

E.g the code can be changed like this
```diff
function sendMintMessage(
    address user_, 
    uint256 amount_, 
    address refundTo_, 
    bytes calldata adapterParams
) external payable onlyDistribution {
    RewardTokenConfig storage config = rewardTokenConfig;

    bytes memory receiverAndSenderAddresses_ = abi.encodePacked(config.receiver, address(this));
    bytes memory payload_ = abi.encode(user_, amount_);

    ILayerZeroEndpoint(config.gateway).send{value: msg.value}( 
        config.receiverChainId, 
        receiverAndSenderAddresses_, 
        payload_, 
        payable(refundTo_), 
        address(0x0), 
+        adapterParams  // Pass adapterParams here
    );
}
```

and from Distribution claim function you can pass the custom settings in `adapterParams`

```solidity
// Example usage in Distribution.sol
L1Sender(l1Sender).sendMintMessage{value: msg.value}(user_, pendingRewards_, _msgSender(), adapterParams);
```
## <a id='L-03'></a>L-03. Create Pool in Mock Distribution is missing validations; allowing duplicates, wrong decreaseInterval value and payoutStart value

_Submitted by [0xTheBlackPanther](/profile/clnca1ftl0000lf08bfytq099), [oualidpro](/profile/clkn61ppo0008l6086a909pio), [greatlake](/profile/clqqqx4vv00008fmhava6pyaf), [chainNue](/profile/clkceb0jn000ol8082eekhkg8), [Auditism](/profile/clk3t8gh1000iib08z1nz6equ), [Night](/profile/cls5z7fis00e4ydp3t24dr3no), [smbv1923](/profile/clkp51djq001amy08d2e1slqf), [Heba](/profile/clo3cb5nv000mmj087plzmqy8). Selected submission by: [0xTheBlackPanther](/profile/clnca1ftl0000lf08bfytq099)._      
				
### Relevant GitHub Links
	
https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/mock/DistributionV2.sol#L18-L20


## Summary
The `createPool` function in the mock `DistributionV2` contract lacks essential validation checks, posing potential risks related to the pool's payout start, decrease interval, and the prevention of duplicate pools. The absence of these checks could lead to unexpected behavior, disruptions, and complexities in managing the system. The recommended checks aim to enhance the robustness and security of the contract.

## Vulnerability Details
1. **Payout Start Validation Missing:**
   - The `createPool` function does not check whether `pool_.payoutStart` is set to a future timestamp. This absence allows the possibility of setting payout start to 0 or a past date.
  
2. **Decrease Interval Validation Missing:**
   - The function does not verify if `pool_.decreaseInterval` is greater than zero. This lack of validation can lead to unexpected behavior, especially if the contract performs calculations involving `decreaseInterval`.

3. **Duplicate Pool Check Missing:**
   - The function does not check for duplicate pools before adding them to the `pools` array. This absence may result in confusion and complexity in managing and maintaining the system, as duplicate pools may be inadvertently added.

4. Even there is no access control, so anyone can call this function.

## Impact
1. **Payout Start Validation Missing:**
   - The absence of a payout start validation check could allow users to set payout start to 0 or a past date. This may impact functions relying on payout start, potentially leading to unexpected behavior.

2. **Decrease Interval Validation Missing:**
   - Lack of validation for `decreaseInterval` may introduce vulnerabilities, impacting calculations and potentially causing transaction reverts or unexpected results.

3. **Duplicate Pool Check Missing:**
   - The absence of a duplicate pool check may lead to confusion and complexities in managing pools, as unintended duplicate entries could be added to the `pools` array.

4. Anyone can call this

## Tools Used
Manual review and analysis 

## Recommendations
1. **Payout Start Validation:**
   - Add the following check to ensure that `payoutStart` is set to a future timestamp:
     ```solidity
     require(pool_.payoutStart > block.timestamp, "DS: invalid payout start value");
     ```

2. **Decrease Interval Validation:**
   - Add the following check to ensure that `decreaseInterval` is greater than zero:
     ```solidity
     require(pool_.decreaseInterval > 0, "DS: invalid decrease interval");
     ```

3. **Duplicate Pool Check:**
   - Implement a check to ensure that duplicate pools are not added to the `pools` array. This can be achieved by verifying the uniqueness of pool attributes before appending a new pool.

4. Add access control. 


## <a id='L-04'></a>L-04. The `editPool()` lacks a sanity check on the `payoutStart` parameter leading to incorrect or unfair reward distributions

_Submitted by [C1rdan](/profile/cls1evv44000goy8lqzjsp86u), [Krace](/profile/clmzp6r0w0000l608cmp45div), [IvanFitro](/profile/clkbfsgal0004me08ro82cg7e), [Silvermist](/profile/clku3kjou0008mr08snycb1tu), [yotov721](/profile/clnubfwv60006l008jd3k83n9), [0xTheBlackPanther](/profile/clnca1ftl0000lf08bfytq099), [chainNue](/profile/clkceb0jn000ol8082eekhkg8), [Tripathi](/profile/clk3xe9tk0024l808xjc9wkg4), [VaRuN](/profile/clkdpp30c000eme08jovtg6xb), [1nc0gn170](/profile/clk9zehwa0000l508h5rx35pc), [serialcoder](/profile/clkb309g90008l208so2bzcy6), [pontifex](/profile/clk3xo3e0000omm08i6ehw2ae). Selected submission by: [serialcoder](/profile/clkb309g90008l208so2bzcy6)._      
				
### Relevant GitHub Links
	
https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/Distribution.sol#L82-L96

## Summary

An admin can update the core parameters of a specific pool via the `Distribution:editPool()`. However, the function lacks a sanity check on the `payoutStart` parameter, leading to incorrect or unfair reward distributions to pool stakers.

## Vulnerability Details

The snippet below presents the [`editPool()`](https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/Distribution.sol#L82-L96). As you can see, the function does not have a sanity check on the `pool_.payoutStart` parameter. Therefore, the `pool_.payoutStart` parameter can be set to an arbitrary timestamp, including the past timestamp.

Suppose the past timestamp is set by mistake. The pool will distribute rewards to stakers by accounting for past staking positions, which can lead to incorrect or unfair reward distribution issues for some stakers.

To elaborate, for instance, if some stakers had unstaked their staking positions before the pool in question was updated, they would lose the rewards even if the reward distribution also accounts for the period of time they had ever staked in the pool. In other words, the pool should not distribute rewards to past staking positions for fair distributions.

```solidity
function editPool(uint256 poolId_, Pool calldata pool_) external onlyOwner poolExists(poolId_) {
    _validatePool(pool_);
    require(pools[poolId_].isPublic == pool_.isPublic, "DS: invalid pool type");

    PoolData storage poolData = poolsData[poolId_];
    uint256 currentPoolRate_ = _getCurrentPoolRate(poolId_);

    // Update pool data
    poolData.rate = currentPoolRate_;
    poolData.lastUpdate = uint128(block.timestamp);

    pools[poolId_] = pool_;

    emit PoolEdited(poolId_, pool_);
}
```

- https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/Distribution.sol#L82-L96

## Impact

Distributing rewards by accounting for past staking positions can lead to incorrect or unfair reward distribution issues for some stakers.

For instance, if some stakers had unstaked their staking positions before the pool was updated, they would lose the rewards even if the reward distribution also accounts for the period of time they had ever staked in the pool. In other words, the pool should not distribute rewards to past staking positions for fair distributions.

## Tools Used

Manual Review

## Recommendations

Add a sanity check on the `pool_.payoutStart` parameter, like the below snippet. The sanity check ensures that the pool cannot distribute rewards to past staking positions for fair reward distributions.

```diff
    function editPool(uint256 poolId_, Pool calldata pool_) external onlyOwner poolExists(poolId_) {
+       require(pool_.payoutStart > block.timestamp, "DS: invalid payout start value");

        _validatePool(pool_);
        require(pools[poolId_].isPublic == pool_.isPublic, "DS: invalid pool type");

        PoolData storage poolData = poolsData[poolId_];
        uint256 currentPoolRate_ = _getCurrentPoolRate(poolId_);

        // Update pool data
        poolData.rate = currentPoolRate_;
        poolData.lastUpdate = uint128(block.timestamp);

        pools[poolId_] = pool_;

        emit PoolEdited(poolId_, pool_);
    }
```
## <a id='L-05'></a>L-05. Do not hardcode `_zroPaymentAddress` field to `address(0)`

_Submitted by [abhishekthakur](/profile/clkaqh5590000k108p39ktfwl), [zigtur](/profile/clknjcwb00000me08tsnr970w), [oualidpro](/profile/clkn61ppo0008l6086a909pio), [MrPotatoMagic](/profile/clk3to00g001cl5087hsgvbey), [Joshuajee](/profile/clp8tjvhb0000r61pfr2owzuy), [kaysoft](/profile/clkig5ndy001cmh08vf2kbcem), [Denzi](/profile/clnvfit56000bl008kg599zbt), [hermit](/profile/clqu3gcjq0000kn29hhqdxinl), [0xsandy](/profile/clk43kus5009imb0830ko7dxy). Selected submission by: [oualidpro](/profile/clkn61ppo0008l6086a909pio)._      
				
### Relevant GitHub Links
	
https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/L1Sender.sol#L124-L138

## Summary
Do not hardcode `_zroPaymentAddress` field to `address(0)`

## Vulnerability Details
When a user call the `claim()` to get its tokens, 
```solidity
    function claim(uint256 poolId_, address user_) external payable poolExists(poolId_) {
        Pool storage pool = pools[poolId_];
        PoolData storage poolData = poolsData[poolId_];
        UserData storage userData = usersData[user_][poolId_];

        require(block.timestamp > pool.payoutStart + pool.claimLockPeriod, "DS: pool claim is locked");

        uint256 currentPoolRate_ = _getCurrentPoolRate(poolId_);
        uint256 pendingRewards_ = _getCurrentUserReward(currentPoolRate_, userData);
        require(pendingRewards_ > 0, "DS: nothing to claim");

        // Update pool data
        poolData.lastUpdate = uint128(block.timestamp);
        poolData.rate = currentPoolRate_;

        // Update user data
        userData.rate = currentPoolRate_;
        userData.pendingRewards = 0;

        // Transfer rewards
        L1Sender(l1Sender).sendMintMessage{value: msg.value}(user_, pendingRewards_, _msgSender());

        emit UserClaimed(poolId_, user_, pendingRewards_);
    }
```

an external call is performed by the function to the `sendMintMessage()` function of the `L1Sender` contract. 
```solidity
    function sendMintMessage(address user_, uint256 amount_, address refundTo_) external payable onlyDistribution {
        RewardTokenConfig storage config = rewardTokenConfig;

        bytes memory receiverAndSenderAddresses_ = abi.encodePacked(config.receiver, address(this));
        bytes memory payload_ = abi.encode(user_, amount_);

        ILayerZeroEndpoint(config.gateway).send{value: msg.value}(
            config.receiverChainId, // communicator LayerZero chainId
            receiverAndSenderAddresses_, // send to this address to the communicator
            payload_, // bytes payload
            payable(refundTo_), // refund address
            address(0x0), // future parameter <== @audit
            bytes("") // adapterParams (see "Advanced Features")
        );
    }
```

this function call also perform an external call to the layerzero function send() with the `_zroPaymentAddress == address(0x0)`

However, setting the `_zroPaymentAddress` field to a fixed value of `address(0x0)` eliminates the possibility for the protocol to adopt the ZRO token as a future fee payment method, particularly considering the potential launch of ZRO in the upcoming year.

For more details about this vulnerability, please take a look at the following links:
[LayerZero Integration Checklist](https://layerzero.gitbook.io/docs/troubleshooting/layerzero-integration-checklist)

## Impact
Limiting the contract flexibility and may cause a DOS if the layerZer contract ever disallow payments others than ZRO token.

## Tools Used
Manual audit

## Recommendations
To enhance flexibility for future fee payments using ZRO tokens, it is advisable to pass the `_zroPaymentAddress` field as an input parameter.
## <a id='L-06'></a>L-06. LayerZeroEndpoint.send() in L1Sender.sol may revert if the user does not provide enough native gas as specified

_Submitted by [oualidpro](/profile/clkn61ppo0008l6086a909pio), [0xDemon](/profile/clqm9tqvx00045lj2c6xi9gvv), [ZanyBonzy](/profile/clk9uu45r0000js08lnm9zbez), [iamandreiski](/profile/clqp2o8oi0003a6nvckl3gop2), [lileth](/profile/clk46om4p001el508li67ukm4), [m4k2](/profile/clk7i797n0004ku08oxz4jl9z), [IceBear](/profile/cllnrqkdu0008lc08luxl02vh), [SanketKogekar](/profile/clk3xu7fc0010mm08wnt4txcd), [0xhals](/profile/clkfub7qh0002l508bt5xdugv), [crypticdefense](/profile/clre36taz0000xrkl17g03dfd), [MrPotatoMagic](/profile/clk3to00g001cl5087hsgvbey), [chainNue](/profile/clkceb0jn000ol8082eekhkg8), [greatlake](/profile/clqqqx4vv00008fmhava6pyaf), [1nc0gn170](/profile/clk9zehwa0000l508h5rx35pc), [0xRizwan](/profile/clk7o7bq3000ome08az33iib2), [Denzi](/profile/clnvfit56000bl008kg599zbt). Selected submission by: [0xDemon](/profile/clqm9tqvx00045lj2c6xi9gvv)._      
				
### Relevant GitHub Links
	
https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/Distribution.sol#L174

https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/L1Sender.sol#L130-L137

## Summary

When a user wants to claim the `MOR` token reward on `L2 Arbitrum`, the user interacts with the [`claim`](https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/Distribution.sol#L154-L177) function on `Distribution.sol`. Then, after all the claim requirements have been fulfilled by the user, `Distribution` call the [`L1Sender.sol`](https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/L1Sender.sol#L124-L138) which sends a message via the `LayerZero` endpoint with the send function and if successful it will be received by the `L2MessageReceiver.sol` and will mint the `MOR` token to the user's address on `L2 Arbitrum` as a reward.

The problem here is `{value : msg.value}`  on [`send`](https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/Distribution.sol#L174) function is not set in the codebase so that if the user sends a fee that is less than what is required for execution on the destination chain then the transaction will revert.

## Vulnerability Details

Scenario :

Alice has deposited tokens into a pool on `Distribution.sol`. Over time, Alice has accrued reward tokens through the pool's staking mechanism. Alice then decides to claim her accumulated rewards.

**Steps:**

1. **Alice calls the `claim` function:**
    - Alice specifies the pool ID and her own address.
    - Alice also need to specify the amount of ether she wants to send for gas or include as part of the reward.
2. **Function execution:**
    - The function checks if the claim period has elapsed (e.g., 24 hours since the last claim) and if Alice has any pending rewards.
    - If eligible, the function calculates Alice's current pending rewards based on the pool's reward rate and her deposited tokens.
    - The function updates pool and user data, resetting Alice's pending rewards and recording the current timestamp and rate.
    - Finally, the function calls theÂ `L1Sender.sendMintMessage`Â with the following parameters:
        - `user_`: Alice's address (to mint the reward tokens)
        - `pendingRewards_`: The calculated amount of rewards
        - `_msgSender()`: The address of the contract calling the function
3. **Transaction revert**:
    - Back to claim step point number 2, Alice did not provide enough native gas fee for executing transaction on destination chain. This can cause transaction revert.

Based on `LayerZero` [docs](https://layerzero.gitbook.io/docs/evm-guides/master/how-to-send-a-message), `{value : msg.value}`  on `send` function must be set or it will be revert because user not provide enough gas. 

> You will note in the topmost example we call `send()` with `{value: msg.value}` this is because `send()` requires a bit of  native gas token so the relayer can complete the message delivery on the destination chain. If you don't set this value [you might get this error](https://www.notion.so/docs/troubleshooting/error-messages/error-layerzero-relayer-fee-failed) when calling `endpoint.send()`
> 

## POC

In this coded `POC` , assume the user has passed all the requirements to claim the `MOR` token reward. But the user does not pay enough native gas to execute the transaction on the destination chain which causes the transaction to revert.

```solidity
it('should revert if msg.value less than required to pay gas', async () => {
      await setNextTime(oneHour * 2);
      await distribution.connect(SECOND).stake(poolId, wei(1));

      // Claim after 2 days
      await setNextTime(oneDay + oneDay * 2);
			// User provide less than required and lead to transaction revert 
      await expect (distribution.claim(poolId, SECOND, { value: wei(0.01) })).to.be.revertedWith('LayerZeroMock: not enough native for fees');
    });
```

Result :

```solidity
Distribution
    #claim
      âœ” should revert if msg.value less than required to pay gas (96ms)

  1 passing (2s)
```

This coded `POC` was written using the default environment of the protocol so just input the `Distribution.test.ts` file and paste it in the claim section then the `POC` can be executed immediately.

## Impact

`claim` function will revert and can't be used, user loss the `gasfee` and not receive the reward token yet.

## Tools Used

Manual Review

## Recommended Mitigation

Consider using the [`estimateFees()`](https://layerzero.gitbook.io/docs/evm-guides/contract-standards/estimating-message-fees) function to estimate fees so that the `send()` execution not revert because not enough native gas fee.

The implementation :

```solidity
Contract : L1Sender.sol

// @notice gets a quote in source native gas, for the amount that send() requires to pay for message delivery
    // @param _dstChainId - the destination chain identifier
    // @param _userApplication - the user app address on this EVM chain
    // @param _payload - the custom message to send over LayerZero
    // @param _payInZRO - if false, user app pays the protocol fee in native token
    // @param _adapterParam - parameters for the adapter service, e.g. send some dust native token to dstChain
    function estimateFees(
        uint16 _dstChainId,
        address _userApplication,
        bytes calldata _payload,
        bool _payInZRO,
        bytes calldata _adapterParam
    ) external view returns (uint nativeFee, uint zroFee);

Contract : Distribution.sol

function claim(uint256 poolId_, address user_) external payable poolExists(poolId_) {
        Pool storage pool = pools[poolId_];
        PoolData storage poolData = poolsData[poolId_];
        UserData storage userData = usersData[user_][poolId_];

        require(block.timestamp > pool.payoutStart + pool.claimLockPeriod, "DS: pool claim is locked");

        uint256 currentPoolRate_ = _getCurrentPoolRate(poolId_);
        uint256 pendingRewards_ = _getCurrentUserReward(currentPoolRate_, userData);
        require(pendingRewards_ > 0, "DS: nothing to claim");

        // Update pool data
        poolData.lastUpdate = uint128(block.timestamp);
        poolData.rate = currentPoolRate_;

        // Update user data
        userData.rate = currentPoolRate_;
        userData.pendingRewards = 0;

        // Transfer rewards
				(uint fee, ) = L1Sender.estimateFees;
        L1Sender(l1Sender).sendMintMessage{value: fee}(user_, pendingRewards_, _msgSender());

        emit UserClaimed(poolId_, user_, pendingRewards_);
    }
```
## <a id='L-07'></a>L-07. Users are unable to withdraw immediately, even if they stake after reaching maxEndTime

_Submitted by [Krace](/profile/clmzp6r0w0000l608cmp45div), [0xhals](/profile/clkfub7qh0002l508bt5xdugv). Selected submission by: [Krace](/profile/clmzp6r0w0000l608cmp45div)._      
				
### Relevant GitHub Links
	
https://github.com/Cyfrin/2024-01-Morpheus/blob/76898177fbedcbbf4b78b513d9fa151bbf3388de/contracts/Distribution.sol#L194-L227

https://github.com/Cyfrin/2024-01-Morpheus/blob/76898177fbedcbbf4b78b513d9fa151bbf3388de/contracts/Distribution.sol#L242-L248

## Summary
Users can still stake stETH in the pool after the pool's maxEndTime, but they won't receive any rewards. Withdrawal of these stETH funds necessitates users to wait for the `withdrawLockPeriodAfterStake` duration. In essence, users lock up their stETH for a specific period but do not receive any returns.

## Vulnerability Details

Users could still stake even if the pool's `maxEndTime` has reached, this will update the `lastStake` to the current `block.timestamp`. 
```solidity
    function _stake(address user_, uint256 poolId_, uint256 amount_, uint256 currentPoolRate_) private {
        require(amount_ > 0, "DS: nothing to stake");

        Pool storage pool = pools[poolId_];
        PoolData storage poolData = poolsData[poolId_];
        UserData storage userData = usersData[user_][poolId_];

        if (pool.isPublic) {
            // https://docs.lido.fi/guides/lido-tokens-integration-guide/#steth-internals-share-mechanics
            uint256 balanceBefore_ = IERC20(depositToken).balanceOf(address(this));
            IERC20(depositToken).safeTransferFrom(_msgSender(), address(this), amount_);
            uint256 balanceAfter_ = IERC20(depositToken).balanceOf(address(this));

            amount_ = balanceAfter_ - balanceBefore_;

            require(userData.deposited + amount_ >= pool.minimalStake, "DS: amount too low");

            totalDepositedInPublicPools += amount_;
        }

        userData.pendingRewards = _getCurrentUserReward(currentPoolRate_, userData);

        // Update pool data
        poolData.lastUpdate = uint128(block.timestamp);
        poolData.rate = currentPoolRate_;
        poolData.totalDeposited += amount_;

        // Update user data
        userData.lastStake = uint128(block.timestamp);
        userData.rate = currentPoolRate_;
        userData.deposited += amount_;

        emit UserStaked(poolId_, user_, amount_);
    }
```

Users are unable to receive any rewards as the reward becomes zero after the `maxEndTime`. Additionally, users must wait an extra `withdrawLockPeriodAfterStake` duration to withdraw their stETH.

```solidity
    function _withdraw(address user_, uint256 poolId_, uint256 amount_, uint256 currentPoolRate_) private {
        Pool storage pool = pools[poolId_];
        PoolData storage poolData = poolsData[poolId_];
        UserData storage userData = usersData[user_][poolId_];

        uint256 deposited_ = userData.deposited;
        require(deposited_ > 0, "DS: user isn't staked");

        if (amount_ > deposited_) {
            amount_ = deposited_;
        }

        uint256 newDeposited_;
        if (pool.isPublic) {
            require(
    //@audit users must wait an extra `withdrawLockPeriodAfterStake`
                block.timestamp < pool.payoutStart ||
                    (block.timestamp > pool.payoutStart + pool.withdrawLockPeriod &&
                        block.timestamp > userData.lastStake + pool.withdrawLockPeriodAfterStake),
                "DS: pool withdraw is locked"
            );
            [...]
    }
```


POC:
Add the test to `test/Distribution.test.ts` and run it with `npx hardhat test`.
```diff
diff --git a/test/Distribution.test.ts b/test/Distribution.test.ts
index a08b6f6..af3e00c 100644
--- a/test/Distribution.test.ts
+++ b/test/Distribution.test.ts
@@ -1387,6 +1387,14 @@ describe('Distribution', () => {

       await expect(distribution.withdraw(poolId, wei(0.1))).to.be.revertedWith('DS: pool withdraw is locked');
     });
+
+    it.only("revert when withdrawing, although stake after endTime", async () => {
+      await setNextTime(oneDay * 51);
+
+      await distribution.stake(poolId, wei(1));
+
+      await expect(distribution.withdraw(poolId, wei(0.1))).to.be.revertedWith('DS: pool withdraw is locked');
+    });
   });

   describe('#removeUpgradeability', () => {
```

## Impact
Users can still stake stETH in the pool after the pool's maxEndTime, but they won't receive any rewards. Withdrawal of these stETH funds necessitates users to wait for the `withdrawLockPeriodAfterStake` duration. In essence, users lock up their stETH for a specific period but do not receive any returns.

## Tools Used

hardhat

## Recommendations

Disallow users from staking in pools that have reached maxEndTime.

## <a id='L-08'></a>L-08. L1Sender does not implement `supportsInterface` function

_Submitted by [Timenov](/profile/clkuwlybw001wmk08os9pfnd1)._      
				
### Relevant GitHub Links
	
https://github.com/Cyfrin/2024-01-Morpheus/blob/76898177fbedcbbf4b78b513d9fa151bbf3388de/contracts/L1Sender.sol#L16

## Summary
The contracts `MOR`, `L2TokenReceiver` and `L1Sender` inherit `ERC165`. This standard is used to publish and detect what interfaces a smart contract implements. Read [this](https://eips.ethereum.org/EIPS/eip-165) for more. If we take a look at `MOR` and `L2TokenReceiver`, we can see that they implement this standard the correct way:

```solidity
// MOR.sol

    function supportsInterface(bytes4 interfaceId_) external pure returns (bool) {
        return
            interfaceId_ == type(IMOR).interfaceId ||
            interfaceId_ == type(IERC20).interfaceId ||
            interfaceId_ == type(IERC165).interfaceId;
    }
```

```solidity
// L2TokenReceiver.sol

    function supportsInterface(bytes4 interfaceId_) external pure returns (bool) {
        return interfaceId_ == type(IL2TokenReceiver).interfaceId || interfaceId_ == type(IERC165).interfaceId;
    }
```

But there is no such function in `L1Sender.sol`.

## Vulnerability Details
Having no `supportsInterface` function, means that the `ERC165` standard is not implement correctly. This contract implements `IL1Sender` and `ERC165`. Lets say someone wants to check if this contract implements the `IL1Sender` interface. The lack of `supportsInterface` function, means that the return value will be `false`, which is wrong.

## Impact
When `supportsInterface` is called, the output will always be false.

## Proof of Concept

Do the following changes to `L1Sender.sol`:

- Import the `IERC165` interface at the top of the file:

`import {ERC165, IERC165} from "@openzeppelin/contracts/utils/introspection/ERC165.sol";`

- Create the following pure functions:

```solidity
    function getL1SenderInterface() external pure returns (bytes4) {
        return type(IL1Sender).interfaceId;
    }

    function getIERC165Interface() external pure returns (bytes4) {
        return type(IERC165).interfaceId;
    }
```

Full file can be found in this [Gist](https://gist.github.com/Pavel2202/52f466cc10ffcc96a9ec3a9e529e9485).

Now add the following test cases to `L1Sender.test.ts`

```js
  describe('supportsInterface', () => {
    it('should support l1Sender interface', async () => {
      const l1SenderInterfaceId = await l1Sender.getL1SenderInterface();
      expect(await l1Sender.supportsInterface(l1SenderInterfaceId)).to.be.true;
    });

    it('should support IERC165 interface', async () => {
      const erc165InterfaceId = await l1Sender.getIERC165Interface();
      expect(await l1Sender.supportsInterface(erc165InterfaceId)).to.be.true;
    });
  });
```

Run `npx hardhat test`. 

```solidity
  L1Sender
    supportsInterface
      1) should support l1Sender interface
      âœ” should support IERC165 interface
```

As we can see, the first test fails(which is the `IL1Sender`) and the second(`IERC165`) passes. The second passes because in `ERC165` the `supportsInterface` functions is this:

```solidity
    function supportsInterface(bytes4 interfaceId) public view virtual override returns (bool) {
        return interfaceId == type(IERC165).interfaceId;
    }
```

However this is not the expected behaviour. Both of the tests should pass.

## Tools Used
Manual Review, Hardhat

## Recommendations
Make sure to implement correctly the `supportsInterface` function:

```solidity
    function supportsInterface(bytes4 interfaceId_) public override pure returns (bool) {
        return interfaceId_ == type(IL1Sender).interfaceId || interfaceId_ == type(IERC165).interfaceId;
    }
```

Note that we add a check for `IERC165` here as well, because this function is `override`.

Now run `npx hardhat test` again:

```solidity
  L1Sender
    supportsInterface
      âœ” should support l1Sender interface
      âœ” should support IERC165 interface
```
## <a id='L-09'></a>L-09. 8 lows for mocks

_Submitted by [greatlake](/profile/clqqqx4vv00008fmhava6pyaf), [0x11singh99](/profile/clkhsr7bn0000l608c9vc7ugr), [pontifex](/profile/clk3xo3e0000omm08i6ehw2ae). Selected submission by: [pontifex](/profile/clk3xo3e0000omm08i6ehw2ae)._      
				
### Relevant GitHub Links
	
https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/mock/tokens/WStETHMock.sol#L26

https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/mock/SwapRouterMock.sol#L8-L12

https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/mock/NonfungiblePositionManagerMock.sol#L7-L9

## L-1/8. The `WStETHMock.wrap` function returns `stETHAmount_` variable instead of `wstETHAmount` 
## Relevant GitHub Links
https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/mock/tokens/WStETHMock.sol#L26
## Summary
The `WStETHMock.wrap` function should return `wstETHAmount`, but returns a received `stETHAmount_` variable. This inconsistency with the original function can cause issues with test improvements.
## Vulnerability Details
The original `wrap` function returns `wstETHAmount`:
```solidity
    function wrap(uint256 _stETHAmount) external returns (uint256) {
        require(_stETHAmount > 0, "wstETH: can't wrap zero stETH");
        uint256 wstETHAmount = stETH.getSharesByPooledEth(_stETHAmount);
        _mint(msg.sender, wstETHAmount);
        stETH.transferFrom(msg.sender, address(this), _stETHAmount);
        return wstETHAmount;
    }
```
https://etherscan.io/token/0x7f39c581f595b53c5cb19bd0b3f8da6c935e2ca0#code
The `WStETHMock.wrap` function returns `stETHAmount_`:
```solidity
    function wrap(uint256 stETHAmount_) external returns (uint256) {
        require(stETHAmount_ > 0, "wstETH: can't wrap zero stETH");
        _mint(msg.sender, stETHAmount_);
        stETH.transferFrom(msg.sender, address(this), stETHAmount_);
        return stETHAmount_;
    }
```
## Impact
Inconsistency with the original function case issues with test improvements.
## Tools used
Manual Review
## Recommendations
Consider announcing and returning the `wstETHAmount` variable.



## L-2/8. The `SwapRouterMock.exactInputSingle` function returns `params_.amountIn` variable instead of `amountOut` 
## Relevant GitHub Links
https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/mock/SwapRouterMock.sol#L12
## Summary
The `SwapRouterMock.exactInputSingle` function should return `amountOut`, but returns a received `params_.amountIn` variable. This inconsistency with the original function can cause issues with test improvements.
## Vulnerability Details
The original `exactInputSingle` function returns `amountOut`:
```solidity
    function exactInputSingle(ExactInputSingleParams calldata params)
        external
        payable
        override
        checkDeadline(params.deadline)
        returns (uint256 amountOut)
    {
```
https://github.com/Uniswap/v3-periphery/blob/697c2474757ea89fec12a4e6db16a574fe259610/contracts/SwapRouter.sol#L120
The `SwapRouterMock.exactInputSingle` function returns `params_.amountIn`
```solidity
    function exactInputSingle(ISwapRouter.ExactInputSingleParams calldata params_) external returns (uint256) {
        IERC20(params_.tokenIn).transferFrom(msg.sender, address(this), params_.amountIn);
        IERC20(params_.tokenOut).transfer(params_.recipient, params_.amountIn);

        return params_.amountIn;
    }
```
## Impact
Inconsistency with the original function case issues with test improvements.
## Tools used
Manual Review
## Recommendations
Consider announcing and returning the `amountOut` variable.


## L-3/8. The `SwapRouterMock.exactInputSingle` function does not revert if `tokenIn == tokenOut`
## Relevant GitHub Links
https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/mock/SwapRouterMock.sol#L8-L12
## Summary
The `SwapRouterMock.exactInputSingle` function does not revert if `tokenIn == tokenOut`. This invariant can not be checked.
## Vulnerability Details
There is an revert in the execution flow of the original function:
```solidity
    function computeAddress(address factory, PoolKey memory key) internal pure returns (address pool) {
        require(key.token0 < key.token1);
```
https://github.com/Uniswap/v3-periphery/blob/697c2474757ea89fec12a4e6db16a574fe259610/contracts/libraries/PoolAddress.sol#L33-L34
## Impact
The `tokenIn == tokenOut` invariant can not be checked.
## Tools used
Manual Review
## Recommendations
Consider adding the corresponding check.


## L-4/8. The `SwapRouterMock.exactInputSingle` function does not check deadline
## Relevant GitHub Links
https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/mock/SwapRouterMock.sol#L8-L12
## Summary
The `SwapRouterMock.exactInputSingle` function does not check the deadline with `checkDeadLine`. This invariant can not be checked.
## Vulnerability Details
The original `exactInputSingle` function has the `checkDeadline` modifier:
```solidity
    function exactInputSingle(ExactInputSingleParams calldata params)
        external
        payable
        override
        checkDeadline(params.deadline)
        returns (uint256 amountOut)
    {
```
https://github.com/Uniswap/v3-periphery/blob/697c2474757ea89fec12a4e6db16a574fe259610/contracts/SwapRouter.sol#L119
## Impact
The incorrect deadline invariant can not be checked.
## Tools used
Manual Review
## Recommendations
Consider adding the corresponding check.


## L-5/8. The `SwapRouterMock.exactInputSingle` function does not check `amountOut >= params.amountOutMinimum`
## Relevant GitHub Links
https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/mock/SwapRouterMock.sol#L8-L12
## Summary
The `SwapRouterMock.exactInputSingle` function does not check `amountOut >= params.amountOutMinimum`. This invariant can not be checked.
## Vulnerability Details
The original `exactInputSingle` function has the `amountOut >= params.amountOutMinimum` require:
```solidity
    function exactInputSingle(ExactInputSingleParams calldata params)
...
        require(amountOut >= params.amountOutMinimum, 'Too little received');
    }
```
https://github.com/Uniswap/v3-periphery/blob/697c2474757ea89fec12a4e6db16a574fe259610/contracts/SwapRouter.sol#L128
## Impact
The insufficient `amountOut` invariant can not be checked.
## Tools used
Manual Review
## Recommendations
Consider adding the corresponding check.


## L-6/8. The `SNonfungiblePositionManagerMock.increaseLiquidity` function does not check deadline
## Relevant GitHub Links
https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/mock/NonfungiblePositionManagerMock.sol#L7-L9
## Summary
The `SNonfungiblePositionManagerMock.increaseLiquidity` function does not check the deadline with `checkDeadLine`. This invariant can not be checked.
## Vulnerability Details
The original `increaseLiquidity` function has the `checkDeadline` modifier:
```solidity
    function increaseLiquidity(IncreaseLiquidityParams calldata params)
        external
        payable
        override
        checkDeadline(params.deadline)
        returns (
    {
```
https://github.com/Uniswap/v3-periphery/blob/697c2474757ea89fec12a4e6db16a574fe259610/contracts/NonfungiblePositionManager.sol#L202
## Impact
The incorrect deadline invariant can not be checked.
## Tools used
Manual Review
## Recommendations
Consider adding the corresponding check.


## L-7/8. The `SNonfungiblePositionManagerMock.increaseLiquidity` function does not check `amount0 >= params.amount0Min && amount1 >= params.amount1Min`
## Relevant GitHub Links
https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/mock/SwapRouterMock.sol#L8-L12
## Summary
The `SNonfungiblePositionManagerMock.increaseLiquidity` function does not check `amount0 >= params.amount0Min && amount1 >= params.amount1Min`. This invariant can not be checked.
## Vulnerability Details
The execution flow of the original function has the `amount0 >= params.amount0Min && amount1 >= params.amount1Min` require:
```solidity
        require(amount0 >= params.amount0Min && amount1 >= params.amount1Min, 'Price slippage check');
```
https://github.com/Uniswap/v3-periphery/blob/697c2474757ea89fec12a4e6db16a574fe259610/contracts/base/LiquidityManagement.sol#L88
## Impact
The max price slippage invariant can not be checked.
## Tools used
Manual Review
## Recommendations
Consider adding the corresponding check.


## L-8/8. The `SNonfungiblePositionManagerMock.increaseLiquidity` function does not revert if the `tokenId` is incorrect
## Relevant GitHub Links
https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/mock/SwapRouterMock.sol#L8-L12
## Summary
The `SNonfungiblePositionManagerMock.increaseLiquidity` function does not does not revert if the `tokenId` is incorrect. This invariant can not be checked.
## Impact
The incorrect `tokenId` invariant can not be checked.
## Tools used
Manual Review
## Recommendations
Consider adding the corresponding check.
## <a id='L-10'></a>L-10. 8 lows for mocks

_Submitted by [pontifex](/profile/clk3xo3e0000omm08i6ehw2ae)._      
				
### Relevant GitHub Links
	
https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/mock/tokens/WStETHMock.sol#L26

https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/mock/SwapRouterMock.sol#L8-L12

https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/mock/NonfungiblePositionManagerMock.sol#L7-L9

## L-1/8. The `WStETHMock.wrap` function returns `stETHAmount_` variable instead of `wstETHAmount` 
## Relevant GitHub Links
https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/mock/tokens/WStETHMock.sol#L26
## Summary
The `WStETHMock.wrap` function should return `wstETHAmount`, but returns a received `stETHAmount_` variable. This inconsistency with the original function can cause issues with test improvements.
## Vulnerability Details
The original `wrap` function returns `wstETHAmount`:
```solidity
    function wrap(uint256 _stETHAmount) external returns (uint256) {
        require(_stETHAmount > 0, "wstETH: can't wrap zero stETH");
        uint256 wstETHAmount = stETH.getSharesByPooledEth(_stETHAmount);
        _mint(msg.sender, wstETHAmount);
        stETH.transferFrom(msg.sender, address(this), _stETHAmount);
        return wstETHAmount;
    }
```
https://etherscan.io/token/0x7f39c581f595b53c5cb19bd0b3f8da6c935e2ca0#code
The `WStETHMock.wrap` function returns `stETHAmount_`:
```solidity
    function wrap(uint256 stETHAmount_) external returns (uint256) {
        require(stETHAmount_ > 0, "wstETH: can't wrap zero stETH");
        _mint(msg.sender, stETHAmount_);
        stETH.transferFrom(msg.sender, address(this), stETHAmount_);
        return stETHAmount_;
    }
```
## Impact
Inconsistency with the original function case issues with test improvements.
## Tools used
Manual Review
## Recommendations
Consider announcing and returning the `wstETHAmount` variable.



## L-2/8. The `SwapRouterMock.exactInputSingle` function returns `params_.amountIn` variable instead of `amountOut` 
## Relevant GitHub Links
https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/mock/SwapRouterMock.sol#L12
## Summary
The `SwapRouterMock.exactInputSingle` function should return `amountOut`, but returns a received `params_.amountIn` variable. This inconsistency with the original function can cause issues with test improvements.
## Vulnerability Details
The original `exactInputSingle` function returns `amountOut`:
```solidity
    function exactInputSingle(ExactInputSingleParams calldata params)
        external
        payable
        override
        checkDeadline(params.deadline)
        returns (uint256 amountOut)
    {
```
https://github.com/Uniswap/v3-periphery/blob/697c2474757ea89fec12a4e6db16a574fe259610/contracts/SwapRouter.sol#L120
The `SwapRouterMock.exactInputSingle` function returns `params_.amountIn`
```solidity
    function exactInputSingle(ISwapRouter.ExactInputSingleParams calldata params_) external returns (uint256) {
        IERC20(params_.tokenIn).transferFrom(msg.sender, address(this), params_.amountIn);
        IERC20(params_.tokenOut).transfer(params_.recipient, params_.amountIn);

        return params_.amountIn;
    }
```
## Impact
Inconsistency with the original function case issues with test improvements.
## Tools used
Manual Review
## Recommendations
Consider announcing and returning the `amountOut` variable.


## L-3/8. The `SwapRouterMock.exactInputSingle` function does not revert if `tokenIn == tokenOut`
## Relevant GitHub Links
https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/mock/SwapRouterMock.sol#L8-L12
## Summary
The `SwapRouterMock.exactInputSingle` function does not revert if `tokenIn == tokenOut`. This invariant can not be checked.
## Vulnerability Details
There is an revert in the execution flow of the original function:
```solidity
    function computeAddress(address factory, PoolKey memory key) internal pure returns (address pool) {
        require(key.token0 < key.token1);
```
https://github.com/Uniswap/v3-periphery/blob/697c2474757ea89fec12a4e6db16a574fe259610/contracts/libraries/PoolAddress.sol#L33-L34
## Impact
The `tokenIn == tokenOut` invariant can not be checked.
## Tools used
Manual Review
## Recommendations
Consider adding the corresponding check.


## L-4/8. The `SwapRouterMock.exactInputSingle` function does not check deadline
## Relevant GitHub Links
https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/mock/SwapRouterMock.sol#L8-L12
## Summary
The `SwapRouterMock.exactInputSingle` function does not check the deadline with `checkDeadLine`. This invariant can not be checked.
## Vulnerability Details
The original `exactInputSingle` function has the `checkDeadline` modifier:
```solidity
    function exactInputSingle(ExactInputSingleParams calldata params)
        external
        payable
        override
        checkDeadline(params.deadline)
        returns (uint256 amountOut)
    {
```
https://github.com/Uniswap/v3-periphery/blob/697c2474757ea89fec12a4e6db16a574fe259610/contracts/SwapRouter.sol#L119
## Impact
The incorrect deadline invariant can not be checked.
## Tools used
Manual Review
## Recommendations
Consider adding the corresponding check.


## L-5/8. The `SwapRouterMock.exactInputSingle` function does not check `amountOut >= params.amountOutMinimum`
## Relevant GitHub Links
https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/mock/SwapRouterMock.sol#L8-L12
## Summary
The `SwapRouterMock.exactInputSingle` function does not check `amountOut >= params.amountOutMinimum`. This invariant can not be checked.
## Vulnerability Details
The original `exactInputSingle` function has the `amountOut >= params.amountOutMinimum` require:
```solidity
    function exactInputSingle(ExactInputSingleParams calldata params)
...
        require(amountOut >= params.amountOutMinimum, 'Too little received');
    }
```
https://github.com/Uniswap/v3-periphery/blob/697c2474757ea89fec12a4e6db16a574fe259610/contracts/SwapRouter.sol#L128
## Impact
The insufficient `amountOut` invariant can not be checked.
## Tools used
Manual Review
## Recommendations
Consider adding the corresponding check.


## L-6/8. The `SNonfungiblePositionManagerMock.increaseLiquidity` function does not check deadline
## Relevant GitHub Links
https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/mock/NonfungiblePositionManagerMock.sol#L7-L9
## Summary
The `SNonfungiblePositionManagerMock.increaseLiquidity` function does not check the deadline with `checkDeadLine`. This invariant can not be checked.
## Vulnerability Details
The original `increaseLiquidity` function has the `checkDeadline` modifier:
```solidity
    function increaseLiquidity(IncreaseLiquidityParams calldata params)
        external
        payable
        override
        checkDeadline(params.deadline)
        returns (
    {
```
https://github.com/Uniswap/v3-periphery/blob/697c2474757ea89fec12a4e6db16a574fe259610/contracts/NonfungiblePositionManager.sol#L202
## Impact
The incorrect deadline invariant can not be checked.
## Tools used
Manual Review
## Recommendations
Consider adding the corresponding check.


## L-7/8. The `SNonfungiblePositionManagerMock.increaseLiquidity` function does not check `amount0 >= params.amount0Min && amount1 >= params.amount1Min`
## Relevant GitHub Links
https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/mock/SwapRouterMock.sol#L8-L12
## Summary
The `SNonfungiblePositionManagerMock.increaseLiquidity` function does not check `amount0 >= params.amount0Min && amount1 >= params.amount1Min`. This invariant can not be checked.
## Vulnerability Details
The execution flow of the original function has the `amount0 >= params.amount0Min && amount1 >= params.amount1Min` require:
```solidity
        require(amount0 >= params.amount0Min && amount1 >= params.amount1Min, 'Price slippage check');
```
https://github.com/Uniswap/v3-periphery/blob/697c2474757ea89fec12a4e6db16a574fe259610/contracts/base/LiquidityManagement.sol#L88
## Impact
The max price slippage invariant can not be checked.
## Tools used
Manual Review
## Recommendations
Consider adding the corresponding check.


## L-8/8. The `SNonfungiblePositionManagerMock.increaseLiquidity` function does not revert if the `tokenId` is incorrect
## Relevant GitHub Links
https://github.com/Cyfrin/2024-01-Morpheus/blob/07c900d22073911afa23b7fa69a4249ab5b713c8/contracts/mock/SwapRouterMock.sol#L8-L12
## Summary
The `SNonfungiblePositionManagerMock.increaseLiquidity` function does not does not revert if the `tokenId` is incorrect. This invariant can not be checked.
## Impact
The incorrect `tokenId` invariant can not be checked.
## Tools used
Manual Review
## Recommendations
Consider adding the corresponding check.




