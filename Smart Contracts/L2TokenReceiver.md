# L2TokenReceiver

`L2TokenReceiver.sol` is a component of the Techno Capital Machine. It is responsible for receiving wstETH yield from [`L1Sender`](L1Sender.md) via the native Arbitrum bridge and managing Protocol-Owned Liquidity.

All functions on `L2TokenReceiver` can only be called by the contract owner – the Morpheus multisig.

## Variables

| Name                         | Type                        | Description                                                                                                     |
|------------------------------|-----------------------------|-----------------------------------------------------------------------------------------------------------------|
| `router`                     | address                     | Address of the Uniswap V3 router.                                                                               |
| `nonfungiblePositionManager` | address                     | Address of the Uniswap V3 Nonfungible Position Manager.                                                         |
| `params`                     | [`SwapParams`](#swapparams) | Parameters used for swaps, including the wrapped deposit token, reward token, pair fee, and slippage tolerance. |

## Functions

### swap

```solidity
function swap(
    uint256 amountIn_,
    uint256 amountOutMinimum_,
    uint256 deadline_
    ) external onlyOwner returns (uint256)
```

Executes a token swap on Uniswap V3 using specified parameters. Used to swap wstETH for MOR.

#### Parameters:

| Name                | Type    | Description                                    |
|---------------------|---------|------------------------------------------------|
| `amountIn_`         | uint256 | The amount of input token to swap.             |
| `amountOutMinimum_` | uint256 | The minimum amount of output token to accept.  |
| `deadline_`         | uint256 | Timestamp after which the transaction reverts. |

#### Return Values:

| Type    | Description                                     |
|---------|-------------------------------------------------|
| uint256 | The amount of output tokens received from swap. |

### increaseLiquidityCurrentRange

```solidity
function increaseLiquidityCurrentRange(
    uint256 tokenId_,
    uint256 depositTokenAmountAdd_,
    uint256 rewardTokenAmountAdd_,
    uint256 depositTokenAmountMin_,
    uint256 rewardTokenAmountMin_
    ) external onlyOwner returns (uint128 liquidity_, uint256 amount0_, uint256 amount1_)
```

Increases liquidity in the current range for a Uniswap V3 liquidity position. Used to add MOR/wstETH liquidity.

#### Parameters:

| Name                     | Type    | Description                                                     |
|--------------------------|---------|-----------------------------------------------------------------|
| `tokenId_`               | uint256 | The ID of the NFT position to increase liquidity for.           |
| `depositTokenAmountAdd_` | uint256 | Amount of the wrapped deposit token to add to the position.     |
| `rewardTokenAmountAdd_`  | uint256 | Amount of the reward token to add to the position.              |
| `depositTokenAmountMin_` | uint256 | Minimum amount of the wrapped deposit token that must be added. |
| `rewardTokenAmountMin_`  | uint256 | Minimum amount of the reward token that must be added.          |

#### Return Values:

| Type    | Description                                           |
|---------|-------------------------------------------------------|
| uint128 | The liquidity added to the position.                  |
| uint256 | The amount of the first token added to the position.  |
| uint256 | The amount of the second token added to the position. |

### collectFees

```solidity
function collectFees(
    uint256 tokenId_
    ) external returns (uint256 amount0_, uint256 amount1_)
```

Collects fees for a Uniswap V3 liquidity position.

#### Parameters:

| Name       | Type    | Description                                            |
|------------|---------|--------------------------------------------------------|
| `tokenId_` | uint256 | The ID of the NFT position from which to collect fees. |

#### Return Values:

| Type    | Description                                       |
|---------|---------------------------------------------------|
| uint256 | The amount of the first token collected as fees.  |
| uint256 | The amount of the second token collected as fees. |

### L2TokenReceiver__init

```solidity
function L2TokenReceiver__init(
    address router_,
    address nonfungiblePositionManager_,
    SwapParams memory params_
    ) external initializer
```

Initializes the contract.

#### Parameters:

| Name                          | Type                        | Description                                             |
|-------------------------------|-----------------------------|---------------------------------------------------------|
| `router_`                     | address                     | Address of the Uniswap V3 router.                       |
| `nonfungiblePositionManager_` | address                     | Address of the Uniswap V3 Nonfungible Position Manager. |
| `params_`                     | [`SwapParams`](#swapparams) | Initial parameters for swaps.                           |

### editParams

```solidity
function editParams(
    SwapParams memory newParams_
    ) external onlyOwner
```

Updates the swap parameters.

#### Parameters:

| Name         | Type                        | Description                            |
|--------------|-----------------------------|----------------------------------------|
| `newParams_` | [`SwapParams`](#swapparams) | The new swap parameters to be applied. |

## Events

### TokensSwapped

Emitted when a swap operation is successfully executed.

```solidity
event TokensSwapped(
    address indexed tokenIn,
    address indexed tokenOut,
    uint256 amountIn,
    uint256 amountOut,
    uint256 amountOutMinimum
    )
```

#### Parameters:

| Name               | Type    | Description                                                |
|--------------------|---------|------------------------------------------------------------|
| `tokenIn`          | address | The address of the input token.                            |
| `tokenOut`         | address | The address of the output token.                           |
| `amountIn`         | uint256 | The amount of the input token swapped.                     |
| `amountOut`        | uint256 | The amount of the output token received.                   |
| `amountOutMinimum` | uint256 | The minimum amount of output token specified for the swap. |

---

### LiquidityIncreased

Emitted when liquidity is successfully added to a Uniswap V3 position.

```solidity
event LiquidityIncreased(
    uint256 indexed tokenId,
    uint256 amount0,
    uint256 amount1,
    uint128 liquidity,
    uint256 amount0Min,
    uint256 amount1Min
    )
```

#### Parameters:

| Name         | Type    | Description                                               |
|--------------|---------|-----------------------------------------------------------|
| `tokenId`    | uint256 | The ID of the NFT position to which liquidity was added.  |
| `amount0`    | uint256 | The amount of the first token added.                      |
| `amount1`    | uint256 | The amount of the second token added.                     |
| `liquidity`  | uint128 | The amount of liquidity added to the position.            |
| `amount0Min` | uint256 | The minimum amount of the first token that was required.  |
| `amount1Min` | uint256 | The minimum amount of the second token that was required. |

---

### FeesCollected

Emitted when fees are collected from a Uniswap V3 position.

```solidity
event FeesCollected(
    uint256 indexed tokenId,
    uint256 amount0,
    uint256 amount1
    )
```

#### Parameters:

| Name      | Type    | Description                                              |
|-----------|---------|----------------------------------------------------------|
| `tokenId` | uint256 | The ID of the NFT position from which fees are collected |

## Structs

### SwapParams

```solidity
struct SwapParams {
    address tokenIn;
    address tokenOut;
    uint24 fee;
    uint160 sqrtPriceLimitX96;
}
```

Stores parameters used for swapping between tokens on Uniswap V3.

#### Fields

| Name                | Type    | Description                                                             |
|---------------------|---------|-------------------------------------------------------------------------|
| `tokenIn`           | address | The address of the token to swap from.                                  |
| `tokenOut`          | address | The address of the token to swap to.                                    |
| `fee`               | uint24  | The fee percentage for the swap in hundredths of a basis point.         |
| `sqrtPriceLimitX96` | uint160 | The square root of the price limit. Used to specify slippage tolerance. |
