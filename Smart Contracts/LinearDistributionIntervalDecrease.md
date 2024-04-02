# LinearDistributionIntervalDecrease

[`LinearDistributionIntervalDecrease.sol`](https://github.com/MorpheusAIs/SmartContracts/blob/main/contracts/libs/LinearDistributionIntervalDecrease.sol) is a custom library used by [`Distribution`](Distribution.md) to calculate MOR token rewards for a specified period. It supports linear distribution schedules with stepped decreases at regular intervals.

## Functions

### getPeriodReward

```solidity
function getPeriodReward(
    uint256 initialAmount_,
    uint256 decreaseAmount_,
    uint128 payoutStart_,
    uint128 interval_,
    uint128 startTime_,
    uint128 endTime_
    ) external pure returns (uint256)
```

Calculates and returns the reward amount for a given period and distribution parameters. The calculation accounts for partial intervals pro rata.

#### Parameters

| Name              | Type    | Description                                              |
|-------------------|---------|----------------------------------------------------------|
| `initialAmount_`  | uint256 | The initial reward amount per interval.                  |
| `decreaseAmount_` | uint256 | The amount by which the reward decreases each interval.  |
| `payoutStart_`    | uint128 | The timestamp at which the distribution schedule starts. |
| `interval_`       | uint128 | The duration of each interval in seconds.                |
| `startTime_`      | uint128 | The timestamp at which the period starts.                |
| `endTime_`        | uint128 | The timestamp at which the period ends.                  |

#### Return Values

| Type    | Description                          |
|---------|--------------------------------------|
| uint256 | The reward for the specified period. |