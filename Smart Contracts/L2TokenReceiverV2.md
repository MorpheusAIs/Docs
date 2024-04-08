# L2TokenReceiverV2

[`L2TokenReceiverV2.sol`](https://github.com/MorpheusAIs/SmartContracts/blob/main/contracts/L2TokenReceiverV2.sol) is a component of the Techno Capital Machine. It is responsible for receiving wstETH yield from [`L1Sender`](L1Sender.md) via the native Arbitrum bridge and managing Protocol-Owned Liquidity.

The contract supports swapping tokens with the `swap` method through Uniswap V3 for either of two token pairs specified in `firstSwapParams` and `secondSwapParams`. The former is used to swap bridged wstETH yield for WETH. The latter is used to swap half of the resulting WETH for MOR. In turn, additional liquidity for the MOR/WETH pair is provisioned using the `increaseLiquidityCurrentRange` method.

All functions on `L2TokenReceiverV2` can only be called by the contract owner – the Morpheus multisig.

## Variables

| Name                         | Type                        | Description                                                                                                  |
|------------------------------|-----------------------------|--------------------------------------------------------------------------------------------------------------|
| `router`                     | address                     | Address of the Uniswap V3 router.                                                                            |
| `nonfungiblePositionManager` | address                     | Address of the Uniswap V3 Nonfungible Position Manager.                                                      |
| `secondSwapParams`           | [`SwapParams`](#swapparams) | Uniswap V3 parameters for the MOR/WETH pair, including token addresses, pair fee, and slippage tolerance.    |
| `firstSwapParams`            | [`SwapParams`](#swapparams) | Uniswap V3 parameters for the wstETH/WETH pair, including token addresses, pair fee, and slippage tolerance. |

## Functions

### swap

```solidity
function swap(
    uint256 amountIn_,
    uint256 amountOutMinimum_,
    uint256 deadline_,
    bool isEditFirstParams_
    ) external onlyOwner returns (uint256)
```

Executes a token swap on Uniswap V3 using specified parameters. Used to swap wstETH for WETH or WETH for MOR.

#### Parameters:

| Name                 | Type    | Description                                                                                                                 |
|----------------------|---------|-----------------------------------------------------------------------------------------------------------------------------|
| `amountIn_`          | uint256 | The amount of input token to swap.                                                                                          |
| `amountOutMinimum_`  | uint256 | The minimum amount of output token to accept.                                                                               |
| `deadline_`          | uint256 | Timestamp after which the transaction reverts.                                                                              |
| `isEditFirstParams_` | bool    | Determines if the swap uses `firstSwapParams` (i.e. swaps wstETH for WETH) or `secondSwapParams` (i.e. swaps WETH for MOR). |

#### Return Values:

| Type    | Description                                         |
|---------|-----------------------------------------------------|
| uint256 | The amount of output tokens received from the swap. |

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

Increases liquidity in the current range for a Uniswap V3 liquidity position. Used to add liquidity on the MOR/WETH pair.

#### Parameters:

| Name                     | Type    | Description                                           |
|--------------------------|---------|-------------------------------------------------------|
| `tokenId_`               | uint256 | The ID of the NFT position to increase liquidity for. |
| `depositTokenAmountAdd_` | uint256 | Amount of WETH to add to the position.                |
| `rewardTokenAmountAdd_`  | uint256 | Amount of MOR to add to the position.                 |
| `depositTokenAmountMin_` | uint256 | Minimum amount of WETH that must be added.            |
| `rewardTokenAmountMin_`  | uint256 | Minimum amount of MOR that must be added.             |

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

Collects fees for a Uniswap V3 liquidity position. Used to collect fees from the MOR/WETH pair.

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
    SwapParams memory newParams_,
    bool isEditFirstParams_
    ) external onlyOwner
```

Updates the swap parameters for `firstSwapParams` or `secondSwapParams`.

#### Parameters:

| Name                 | Type                        | Description                                                      |
|----------------------|-----------------------------|------------------------------------------------------------------|
| `newParams_`         | [`SwapParams`](#swapparams) | The new swap parameters to be applied.                           |
| `isEditFirstParams_` | bool                        | Determines if `firstSwapParams` or `secondSwapParams`is updated. |

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
