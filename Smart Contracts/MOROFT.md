# MOROFT

[`MOROFT.sol`](https://github.com/MorpheusAIs/SmartContracts/blob/main/contracts/MOROFT.sol), the Morpheus token, is a [LayerZero Omnichain Fungible Token](https://docs.layerzero.network/v2/developers/evm/oft/quickstart) (OFT). This allows the token to be transferred across [supported networks](https://docs.layerzero.network/v2/developers/evm/technical-reference/endpoints) such as Ethereum, Arbitrum, BNB Chain, and others without the need for wrapping. 

Tokens can only be minted by the immutable `minter_` – [`L2MessageReceiver`](L2MessageReceiver.md) – when claimed by users.

## Functions

*Standard [ERC20](https://docs.openzeppelin.com/contracts/2.x/api/token/erc20) and [OFT](https://docs.layerzero.network/v2/developers/evm/oft/quickstart) functions are not listed below.*

### mint

```solidity
function mint(
    address _account,
    uint256 amount_
    ) external onlyOwner
```

Mints new tokens to the specified account. This function can only be called by the `_minter_` – [`L2MessageReceiver`](L2MessageReceiver.md).

#### Parameters:

| Name       | Type    | Description                             |
|------------|---------|-----------------------------------------|
| `_account` | address | The account to which tokens are minted. |
| `_amount`  | uint256 | The number of tokens to mint.           |

---

### burn

```solidity
function burn(
    uint256 _amount
    ) public override
```

Burns a specified amount of tokens from the caller's account, reducing the total supply.

#### Parameters:

| Name      | Type    | Description                                                        |
|-----------|---------|--------------------------------------------------------------------|
| `_amount` | uint256 | The number of tokens to be burned (removed) from the total supply. |

### burnFrom

```solidity
function burnFrom(
    address _account,
    uint256 _amount
    ) public override
```

Burns a specified amount of tokens from the specified account, reducing the total supply. The caller must have allowance for at least the specified amount of tokens.

#### Parameters:

| Name       | Type    | Description                                                        |
|------------|---------|--------------------------------------------------------------------|
| `_account` | uint256 | The account from which to burn tokens.                             |
| `_amount`  | uint256 | The number of tokens to be burned (removed) from the total supply. |

### minter

```solidity
function minter(
    ) public view returns(address)
```

Returns the address of the `minter_`.

#### Return Values

| Type    | Description                   |
|---------|-------------------------------|
| address | The address of the `minter_`. |