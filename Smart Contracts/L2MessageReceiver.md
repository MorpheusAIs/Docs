# L2MessageReceiver

[`L2MessageReceiver.sol`](https://github.com/MorpheusAIs/SmartContracts/blob/main/contracts/L2MessageReceiver.sol) is an implementation of the [`ILayerZeroReceiver`](https://layerzero.gitbook.io/docs/evm-guides/evm-solidity-interfaces/ilayerzeroreceiver) interface used to receive messages via LayerZero. It receives instructions to mint MOR tokens (e.g. to Capital Providers) from [`L1Sender`](L1Sender.md) on Ethereum.

## Variables

| Name          | Type              | Description                                                   |
|---------------|-------------------|---------------------------------------------------------------|
| `rewardToken` | address           | The address of the wrapped reward token (wstETH) on Arbitrum. |
| `config`      | [Config](#config) | Configuration data for LayerZero messaging.                   |

## Functions

### lzReceive

```solidity
function lzReceive(
    uint16 senderChainId_,
    bytes memory senderAndReceiverAddresses_,
    uint64 nonce_,
    bytes memory payload_
    ) external
```

Mints MOR tokens according to instructions sent by [`L1Sender`](L1Sender.md) via LayerZero. This function is [blocking](https://layerzero.gitbook.io/docs/troubleshooting/faq-1#two-modes-blocking-and-nonblocking).

#### Parameters:

| Name                          | Type   | Description                                                                                                                                 |
|:------------------------------|:-------|:--------------------------------------------------------------------------------------------------------------------------------------------|
| `senderChainId_`              | uint16 | The LayerZero `endpointId` of the sender (101/Ethereum)                                                                                     |
| `senderAndReceiverAddresses_` | bytes  | Concatenated addresses of the sender `L1Sender` and receiver `L2MessageReceiver`.                                                           |
| `nonce_`                      | uint64 | Nonce of the message.                                                                                                                       |
| `payload_`                    | bytes  | Minting instructions sent by `L1Sender`, consisting of an address to mint MOR tokens to and an amount. ABI encoded as `(address, uint256)`. |

### nonblockingLzReceive

```solidity
function nonblockingLzReceive(
    uint16 senderChainId_,
    bytes memory senderAndReceiverAddresses_,
    bytes memory payload_
    ) public
```

Mints MOR tokens according to instructions sent by [`L1Sender`](L1Sender.md) via LayerZero. This function is [non-blocking](https://layerzero.gitbook.io/docs/troubleshooting/faq-1#two-modes-blocking-and-nonblocking).

#### Parameters:

| Name                          | Type   | Description                                                                                                                                 |
|:------------------------------|:-------|:--------------------------------------------------------------------------------------------------------------------------------------------|
| `senderChainId_`              | uint16 | The LayerZero `endpointId` of the sender (101/Ethereum)                                                                                     |
| `senderAndReceiverAddresses_` | bytes  | Concatenated addresses of the sender `L1Sender` and receiver `L2MessageReceiver`.                                                           |
| `payload_`                    | bytes  | Minting instructions sent by `L1Sender`, consisting of an address to mint MOR tokens to and an amount. ABI encoded as `(address, uint256)`. |

### retryMessage

```solidity
function retryMessage(
    uint16 senderChainId_,
    bytes memory senderAndReceiverAddresses_,
    uint64 nonce_,
    bytes memory payload_
    ) external
```

Retries the processing of a previously failed message.

#### Parameters

| Name                          | Type   | Description                                                                                                                                 |
|:------------------------------|:-------|:--------------------------------------------------------------------------------------------------------------------------------------------|
| `senderChainId_`              | uint16 | The LayerZero `endpointId` of the sender (101/Ethereum)                                                                                     |
| `senderAndReceiverAddresses_` | bytes  | Concatenated addresses of the sender `L1Sender` and receiver `L2MessageReceiver`.                                                           |
| `nonce_`                      | uint64 | Nonce of the failed message.                                                                                                                |
| `payload_`                    | bytes  | Minting instructions sent by `L1Sender`, consisting of an address to mint MOR tokens to and an amount. ABI encoded as `(address, uint256)`. |

### L2MessageReceiver__init

```solidity
function L2MessageReceiver__init() external initializer {
    __Ownable_init();
    __UUPSUpgradeable_init();
    }
```

Initializes the contract for ownership and upgradeability.

### setParams

```solidity
function setParams(
    address rewardToken_,
    Config calldata config_
    ) external onlyOwner
```

Sets the parameters of the contract, including the address of the wrapped reward token (wstETH) on Arbitrum and LayerZero configuration settings.

#### Parameters:

| Name           | Type              | Description                                          |
|----------------|-------------------|------------------------------------------------------|
| `rewardToken_` | address           | The address of the wrapped reward token on Arbitrum. |
| `config_`      | [Config](#config) | Config struct containing various parameters.         |

## Structs

### Config

```solidity
struct Config {
    address gateway;
    address sender;
    uint16 senderChainId;
    }
```

Configuration data for LayerZero messaging.

#### Fields

| Name            | Type    | Description                                             |
|-----------------|---------|---------------------------------------------------------|
| `gateway`       | address | The address of the LayerZero gateway on Arbitrum.       |
| `sender`        | address | The address of `L1Sender`.                              |
| `senderChainId` | uint16  | The LayerZero `endpointId` of the sender (101/Ethereum) |