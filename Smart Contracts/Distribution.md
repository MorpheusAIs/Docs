# Distribution

[`Distribution.sol`](https://github.com/MorpheusAIs/SmartContracts/blob/main/contracts/Distribution.sol) is the core contract of the [Techno Capital Machine](../!KEYDOCS%20README%20FIRST!/TechnoCapitalMachineTCM.md). It allows Capital Providers to stake stETH (Lido Staked ETH) on Ethereum and claim MOR rewards to Arbitrum.

`Distribution` utilizes [`L1Sender`](L1Sender.md) to bridge stETH yield and relay MOR claims to Arbitrum. [`LinearDistributionIntervalDecrease`](LinearDistributionIntervalDecrease.md) is used to calculate pool rewards.

## Public Variables

| Name                          | Type              | Description                                                       |
|-------------------------------|-------------------|-------------------------------------------------------------------|
| `depositToken`                | address           | The address of the deposit token on Ethereum (stETH).             |
| `l1Sender`                    | address           | The address of the `L1Sender` contract.                           |
| `pools`                       | [`Pool[]`](#pool) | Configurations for all pools through which rewards are allocated. |
| `poolsData`                   | mapping           | Tracking data for pools.                                          |
| `usersData`                   | mapping           | Tracking data for users.                                          |
| `totalDepositedInPublicPools` | uint256           | The total amount of the deposit token in all public pools.        |

## Functions

### stake

```solidity
function stake(
    uint256 poolId_,
    uint256 amount_
    ) external poolExists(poolId_) poolPublic(poolId_)
```

Allows users to stake the deposit token (stETH) in a public pool.

#### Parameters

| Name      | Type    | Description                            |
|-----------|---------|----------------------------------------|
| `poolId_` | uint256 | The ID of the public pool to stake in. |
| `amount_` | uint256 | The amount of deposit tokens to stake. |

### claim

```solidity
function claim(
    uint256 poolId_,
    address receiver_
    ) external payable poolExists(poolId_)
```

Enables users to claim their MOR rewards from a specific pool. After verifying claims internally, minting instructions are sent to [`L2MessageReceiver`](L2MessageReceiver.md) on Arbitrum via [`L1Sender`](L1Sender.md).

Rewards can only be claimed after the [`claimLockPeriod`](#pool).

#### Parameters

| Name        | Type    | Description                               |
|-------------|---------|-------------------------------------------|
| `poolId_`   | uint256 | The ID of the pool to claim rewards from. |
| `receiver_` | address | The address where rewards are sent.       |

### withdraw

```solidity
function withdraw(
    uint256 poolId_,
    uint256 amount_
    ) external poolExists(poolId_) poolPublic(poolId_)
```

Allows users to withdraw their staked tokens from a public pool.

Withdrawals can only be made after the [`withdrawLockPeriod` and `withdrawLockPeriodAfterStake`](#pool).

#### Parameters

| Name      | Type    | Description                          |
|-----------|---------|--------------------------------------|
| `poolId_` | uint256 | The ID of the pool to withdraw from. |
| `amount_` | uint256 | The amount of tokens to withdraw.    |

### getCurrentUserReward

```solidity
function getCurrentUserReward(
    uint256 poolId_,
    address user_
    ) external view returns (uint256)
```

Calculates and returns the current unclaimed reward amount for a user in a specified pool.

#### Parameters

| Name      | Type    | Description              |
|-----------|---------|--------------------------|
| `poolId_` | uint256 | The ID of the pool.      |
| `user_`   | address | The address of the user. |

#### Return Values

| Type    | Description                                                 |
|---------|-------------------------------------------------------------|
| uint256 | The current unclaimed reward amount for the specified user. |

### Distribution_init

```solidity
function Distribution_init(
    address depositToken_,
    address l1Sender_,
    Pool[] calldata poolsInfo_
    ) external initializer
```

Initializes the contract with the deposit token (stETH) address, [`L1Sender`](L1Sender.md) address, and initial pools.

#### Parameters

| Name            | Type              | Description                             |
|-----------------|-------------------|-----------------------------------------|
| `depositToken_` | address           | The address of the deposit token.       |
| `l1Sender_`     | address           | The address of the `L1Sender` contract. |
| `poolsInfo_`    | [`Pool[]`](#pool) | An array of pools to be initialized.    |

### createPool

```solidity
function createPool(
    Pool calldata pool_
    ) public onlyOwner
```

Creates a new pool based on the provided pool configuration. This function can only be called by the owner of the contract.

#### Parameters

| Name    | Type            | Description                        |
|---------|-----------------|------------------------------------|
| `pool_` | [`Pool`](#pool) | The configuration of the new pool. |

### editPool

```solidity
function editPool(
    uint256 poolId_,
    Pool calldata pool_
    ) external onlyOwner poolExists(poolId_)
```

Edits an existing pool's configuration. This function can only be called by the owner of the contract.

#### Parameters

| Name      | Type            | Description                         |
|-----------|-----------------|-------------------------------------|
| `poolId_` | uint256         | The ID of the pool to be edited.    |
| `pool_`   | [`Pool`](#pool) | The new configuration for the pool. |

### getPeriodReward

```solidity
function getPeriodReward(
    uint256 poolId_,
    uint128 startTime_,
    uint128 endTime_
    ) public view returns (uint256)
```

Calculates the reward for a specified pool and period. Uses the [`LinearDistributionIntervalDecrease`](LinearDistributionIntervalDecrease.md) library.

#### Parameters

| Name         | Type    | Description                        |
|--------------|---------|------------------------------------|
| `poolId_`    | uint256 | The ID of the pool.                |
| `startTime_` | uint128 | The start timestamp of the period. |
| `endTime_`   | uint128 | The end timestamp of the period.   |

#### Return Values

| Type    | Description                             |
|---------|-----------------------------------------|
| uint256 | The total reward amount for the period. |

### manageUsersInPrivatePool

```solidity
function manageUsersInPrivatePool(
    uint256 poolId_,
    address[] calldata users_,
    uint256[] calldata amounts_
    ) external onlyOwner poolExists(poolId_)
```

Manages user stakes in a private pool by adjusting their deposited amounts based on the specified array of amounts. This function can only be called by the owner of the contract.

#### Parameters

| Name       | Type      | Description                                      |
|------------|-----------|--------------------------------------------------|
| `poolId_`  | uint256   | The ID of the private pool to manage users in.   |
| `users_`   | address[] | An array of user addresses to manage stakes for. |
| `amounts_` | uint256[] | An array of amounts corresponding to each user.  |

### overplus

```solidity
function overplus(
    ) public view returns (uint256)
```

Calculates the amount of surplus deposit tokens (stETH yield) in the contract that are not deposited in any pools. These tokens can be bridged to Arbitrum to provision Protocol-Owned Liquidity.

#### Return Values

| Type    | Description                                           |
|---------|-------------------------------------------------------|
| uint256 | The amount of surplus deposit tokens in the contract. |

### bridgeOverplus

```solidity
function bridgeOverplus(
    uint256 gasLimit_,
    uint256 maxFeePerGas_,
    uint256 maxSubmissionCost_
    ) external payable onlyOwner returns (bytes memory)
```

Bridges surplus deposit tokens (stETH yield) to Arbitrum via [`L1Sender`](L1Sender.md). This function can only be called by the owner of the contract.

#### Parameters

| Name                 | Type    | Description                                         |
|----------------------|---------|-----------------------------------------------------|
| `gasLimit_`          | uint256 | The gas limit for the bridging transaction.         |
| `maxFeePerGas_`      | uint256 | The maximum fee per gas unit willing to be paid.    |
| `maxSubmissionCost_` | uint256 | The maximum cost willing to be paid for submission. |

#### Return Values

| Type  | Description                                     |
|-------|-------------------------------------------------|
| bytes | The ABI-encoded Arbitrum inbox sequence number. |

## Events

### PoolCreated

```solidity
event PoolCreated(
    uint256 indexed poolId,
    Pool pool
    )
```

Emitted when a new pool is created.

#### Parameters

| Name     | Type            | Description                                |
|----------|-----------------|--------------------------------------------|
| `poolId` | uint256         | The unique identifier of the created pool. |
| `pool`   | [`Pool`](#pool) | The pool configuration.                    |

### PoolEdited

```solidity
event PoolEdited(
    uint256 indexed poolId,
    Pool pool
    )
```

Emitted when an existing pool's configuration is edited.

#### Parameters

| Name     | Type            | Description                                        |
|----------|-----------------|----------------------------------------------------|
| `poolId` | uint256         | The unique identifier of the pool that was edited. |
| `pool`   | [`Pool`](#pool) | The pool configuration.                            |

### UserStaked

```solidity
event UserStaked(
    uint256 indexed poolId,
    address indexed user,
    uint256 amount
    )
```

Emitted when a user stakes tokens in a pool.

#### Parameters

| Name     | Type    | Description                                    |
|----------|---------|------------------------------------------------|
| `poolId` | uint256 | The ID of the pool in which tokens are staked. |
| `user`   | address | The address of the user who staked tokens.     |
| `amount` | uint256 | The amount of tokens staked by the user.       |

### UserClaimed

```solidity
event UserClaimed(
    uint256 indexed poolId,
    address indexed user,
    address receiver,
    uint256 amount
    )
```

Emitted when a user claims rewards from a pool.

#### Parameters

| Name       | Type    | Description                                                 |
|------------|---------|-------------------------------------------------------------|
| `poolId`   | uint256 | The ID of the pool from which rewards are claimed.          |
| `user`     | address | The address of the user claiming rewards.                   |
| `receiver` | address | The address where the claimed rewards are sent on Arbitrum. |
| `amount`   | uint256 | The amount of rewards claimed by the user.                  |

### UserWithdrawn

```solidity
event UserWithdrawn(
    uint256 indexed poolId,
    address indexed user,
    uint256 amount
    )
```

Emitted when a user withdraws from a pool.

| Name     | Type    | Description                                         |
|----------|---------|-----------------------------------------------------|
| `poolId` | uint256 | The ID of the pool from which tokens are withdrawn. |
| `user`   | address | The address of the user withdrawing tokens.         |
| `amount` | uint256 | The amount of tokens withdrawn by the user.         |

### OverplusBridged

```solidity
event OverplusBridged(
    uint256 amount,
    bytes uniqueId
    )
```

Emitted when surplus deposit tokens are bridged to Arbitrum.

#### Parameters

| Name       | Type    | Description                                             |
|------------|---------|---------------------------------------------------------|
| `amount`   | uint256 | The amount of surplus deposit tokens that were bridged. |
| `uniqueId` | bytes   | The ABI-encoded Arbitrum inbox sequence number.         |

## Structs

### Pool

```solidity
struct Pool {
    uint128 payoutStart;
    uint128 decreaseInterval;
    uint128 withdrawLockPeriod;
    uint128 claimLockPeriod;
    uint128 withdrawLockPeriodAfterStake;
    uint256 initialReward;
    uint256 rewardDecrease;
    uint256 minimalStake;
    bool isPublic;
    }
```

Configuration data for a pool, including reward distribution schedules and lock periods. Also see [`LinearDistributionIntervalDecrease`](LinearDistributionIntervalDecrease.md).

#### Fields

| Name                           | Type    | Description                                                           |
|--------------------------------|---------|-----------------------------------------------------------------------|
| `payoutStart`                  | uint128 | The timestamp at which the distribution schedule starts.              |
| `decreaseInterval`             | uint128 | The duration of each interval in seconds.                             |
| `withdrawLockPeriod`           | uint128 | The period in seconds during which stake cannot be withdrawn.         |
| `claimLockPeriod`              | uint128 | The period in seconds during which rewards cannot be claimed.         |
| `withdrawLockPeriodAfterStake` | uint128 | The lock period after staking during which stake cannot be withdrawn. |
| `initialReward`                | uint256 | The initial reward amount per interval.                               |
| `rewardDecrease`               | uint256 | The amount by which the reward decreases each interval.               |
| `minimalStake`                 | uint256 | The minimum stake amount required for participation in the pool.      |
| `isPublic`                     | bool    | Indicates if the pool is open to the public or private.               |

### PoolData

```solidity
struct PoolData {
    uint128 lastUpdate;
    uint256 rate;
    uint256 totalDeposited;
    }
```

#### Fields

| Name             | Type    | Description                                          |
|------------------|---------|------------------------------------------------------|
| `lastUpdate`     | uint128 | The timestamp of the last update to the pool's data. |
| `rate`           | uint256 | The current reward rate for the pool.                |
| `totalDeposited` | uint256 | The total amount of tokens deposited in the pool.    |

### UserData

```solidity
struct UserData {
    uint128 lastStake;
    uint256 deposited;
    uint256 rate;
    uint256 pendingRewards;
    }
```

#### Fields

| Name             | Type    | Description                                                 |
|------------------|---------|-------------------------------------------------------------|
| `lastStake`      | uint128 | The timestamp when the user last staked tokens in the pool. |
| `deposited`      | uint256 | The amount of tokens the user has deposited in the pool.    |
| `rate`           | uint256 | The current reward rate applicable to the user.             |
| `pendingRewards` | uint256 | The amount of rewards that the user can claim.              |