# L1Sender

[`L1Sender.sol`](https://github.com/MorpheusAIs/SmartContracts/blob/main/contracts/L1Sender.sol) is responsible for sending tokens and messages from Ethereum to Arbitrum. It is called by [`Distribution`](Distribution.md) to:
* Wrap and send the deposit token (stETH) to Arbitrum via the native Arbitrum bridge
* Send instructions to mint MOR to Arbitrum via LayerZero

## Variables

| Name                    | Type                                        | Description                                                    |
|-------------------------|---------------------------------------------|----------------------------------------------------------------|
| `unwrappedDepositToken` | address                                     | The address of the unwrapped deposit token (stETH).            |
| `distribution`          | address                                     | The `Distribution` contract address.                           |
| `rewardTokenConfig`     | [`RewardTokenConfig`](#rewardtokenconfig)   | Configuration settings for the reward token (MOR).             |
| `depositTokenConfig`    | [`DepositTokenConfig`](#deposittokenconfig) | Configuration settings for the wrapped deposit token (wstETH). |

## Functions

### sendDepositToken

```solidity
function sendDepositToken(
    uint256 gasLimit_,
    uint256 maxFeePerGas_,
    uint256 maxSubmissionCost_
    ) external payable onlyDistribution returns (bytes memory)
```

Wraps and sends the deposit token (stETH) to Arbitrum via the Gateway Router. This function can only be called by [`Distribution`](Distribution.md).

#### Parameters

| Name                 | Type    | Description                                                   |
|----------------------|---------|---------------------------------------------------------------|
| `gasLimit_`          | uint256 | The gas limit for the transaction.                            |
| `maxFeePerGas_`      | uint256 | The maximum fee per gas the sender is willing to pay.         |
| `maxSubmissionCost_` | uint256 | The maximum cost the sender is willing to pay for submission. |

#### Return Values

| Type  | Description                                     |
|-------|-------------------------------------------------|
| bytes | The ABI-encoded Arbitrum inbox sequence number. |

### sendMintMessage

```solidity
function sendMintMessage(
    address user_,
    uint256 amount_,
    address refundTo_
    ) external payable onlyDistribution
```

Sends a message to mint reward tokens (MOR) on Arbitrum via LayerZero. This function can only be called by [`Distribution`](Distribution.md).

#### Parameters

| Name        | Type    | Description                                    |
|-------------|---------|------------------------------------------------|
| `user_`     | address | The user address to receive the minted tokens. |
| `amount_`   | uint256 | The amount of tokens to mint.                  |
| `refundTo_` | address | The address to refund any excess payment.      |

### L1Sender__init

```solidity
function L1Sender__init(
    address distribution_,
    RewardTokenConfig calldata rewardTokenConfig_,
    DepositTokenConfig calldata depositTokenConfig_
    ) external initializer
```

Initializes the contract with the [`Distribution`](Distribution.md) address, reward token configuration, and deposit token configuration.

#### Parameters

| Name                  | Type               | Description                                      |
|-----------------------|--------------------|--------------------------------------------------|
| `distribution_`       | address            | The address responsible for distributing tokens. |
| `rewardTokenConfig_`  | RewardTokenConfig  | Configuration settings for the reward token.     |
| `depositTokenConfig_` | DepositTokenConfig | Configuration settings for the deposit token.    |

### setDistribution

```solidity
function setDistribution(
    address distribution_
    ) public onlyOwner
```

Sets the [`Distribution`](Distribution.md) address. This function can only be called by the contract owner.

#### Parameters

| Name            | Type    | Description                              |
|-----------------|---------|------------------------------------------|
| `distribution_` | address | The address of `Distribution` to be set. |

### setRewardTokenConfig

```solidity
function setRewardTokenConfig(
    RewardTokenConfig calldata newConfig_
    ) public onlyOwner
```

Updates the reward token configuration. This function can only be called by the contract owner.

#### Parameters

| Name         | Type                                      | Description                                 |
|--------------|-------------------------------------------|---------------------------------------------|
| `newConfig_` | [`RewardTokenConfig`](#rewardtokenconfig) | The new configuration for the reward token. |

### setDepositTokenConfig

```solidity
function setDepositTokenConfig(
    DepositTokenConfig calldata newConfig_
    ) public onlyOwner
```

Updates the deposit token configuration. This function can only be called by the contract owner.

#### Parameters

| Name         | Type                                        | Description                                  |
|--------------|---------------------------------------------|----------------------------------------------|
| `newConfig_` | [`DepositTokenConfig`](#deposittokenconfig) | The new configuration for the deposit token. |

## Structs

### DepositTokenConfig

```solidity
struct DepositTokenConfig {
    address token;
    address gateway;
    address receiver;
    }
```

Stores configuration data for the deposit token (stETH) and its bridge.

#### Fields

| Name       | Type    | Description                                                            |
|------------|---------|------------------------------------------------------------------------|
| `token`    | address | The address of the wrapped deposit token on Ethereum (wsETH).          |
| `gateway`  | address | The address of the Arbitrum Gateway Router.                            |
| `receiver` | address | The address where tokens are received on Arbitrum (`L2TokenReceiver`). |

### RewardTokenConfig

```solidity
struct RewardTokenConfig {
    address gateway;
    address receiver;
    uint16 receiverChainId;
    address zroPaymentAddress;
    bytes adapterParams;
    }
```

Stores configuration data for the LayerZero messaging bridge.

| Name                | Type    | Description                                                                                                                                |
|---------------------|---------|--------------------------------------------------------------------------------------------------------------------------------------------|
| `gateway`           | address | The address of the LayerZero Ethereum endpoint.                                                                                            |
| `receiver`          | address | The address where messages are received on Arbitrum (`L2MessageReceiver`).                                                                 |
| `receiverChainId`   | uint16  | The LayerZero `endpointId` of Arbitrum (110).                                                                                              |
| `zroPaymentAddress` | address | The address of the ZRO token holder who would pay for the transaction.                                                                     |
| `adapterParams`     | bytes   | LayerZero [Adapter Parameters](https://layerzero.gitbook.io/docs/evm-guides/advanced/relayer-adapter-parameters) for custom functionality. |
