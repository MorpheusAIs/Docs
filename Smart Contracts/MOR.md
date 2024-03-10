# MOR

[`MOR.sol`](https://github.com/MorpheusAIs/SmartContracts/blob/main/contracts/MOR.sol), the Morpheus token, is an OpenZeppelin ERC20 implementation that extends the [`ERC20Capped`](https://docs.openzeppelin.com/contracts/5.x/api/token/erc20#ERC20Capped) and [`ERC20Burnable`](https://docs.openzeppelin.com/contracts/5.x/api/token/erc20#ERC20Burnable) extensions.

New tokens can only be minted by the contract owner – [`L2MessageReceiver`](L2MessageReceiver.md) – up to the immutable cap of 42,000,000 tokens.

## Public Variables

| Name  | Type    | Description                                                   |
|-------|---------|---------------------------------------------------------------|
| `cap` | uint256 | The maximum number of tokens that can be minted (42,000,000). |

## Functions

*Standard [ERC20](https://docs.openzeppelin.com/contracts/2.x/api/token/erc20) and [Ownable](https://docs.openzeppelin.com/contracts/2.x/api/ownership#Ownable) functions are not listed below.*

### mint

```solidity
function mint(
    address account_,
    uint256 amount_
    ) external onlyOwner
```

Mints new tokens to the specified account. This function can only be called by the contract owner – [`L2MessageReceiver`](L2MessageReceiver.md).

#### Parameters:

| Name       | Type    | Description                             |
|------------|---------|-----------------------------------------|
| `account_` | address | The account to which tokens are minted. |
| `amount_`  | uint256 | The number of tokens to mint.           |

---

### burn

```solidity
function burn(
    uint256 amount_
    ) public override
```

Burns a specified amount of tokens from the caller's account, reducing the total supply.

#### Parameters:

| Name      | Type    | Description                                                        |
|-----------|---------|--------------------------------------------------------------------|
| `amount_` | uint256 | The number of tokens to be burned (removed) from the total supply. |