# **Tokens on Solana Network**

## **Creating a Token on Solana Network**

```bash
$ spl-token create-token --url devnet

Creating token BigWcBZAgDUTY2XpDYn46DPUSKDJuJ4mG9LYiDKuBjWh

Signature: 3oCaE9ubTtiQtaK2hNfBo9ipMvKZZLV1wgaAhdg1XmGfJBMgWhUnv27p9PdFMD4nvdY1kqTMjqX8pwQJpq7rsWuF
```

This unique address (the one as an example is BigWcBZAgDUTY2XpDYn46DPUSKDJuJ4mG9LYiDKuBjWh) is the token address

## **Minting a Token on Solana Network**

Accounts are files stored on the blockchain.

In order to hold a specific token created on Solana network, we need to have an account for that specific token.

```bash
$ spl-token create-account BigWcBZAgDUTY2XpDYn46DPUSKDJuJ4mG9LYiDKuBjWh --url devnet

Creating account 4RQQyBadpcr....7Efwy

Signature: 3qmp12XyhKa2...231aBxR2qAo8z
```

The account (one with 4RQQyBadpcr....7Efwy) is created specifically for the token (BigWcBZAgDUTY2XpDYn46DPUSKDJuJ4mG9LYiDKuBjWh)

You can check the balance of the token:

```bash
$ spl-token balance BigWcBZAgDUTY2XpDYn46DPUSKDJuJ4mG9LYiDKuBjWh --url devnet
0
```

You will see that the token balance is zero. So we need to increase the token balance. Increasing the token balance is called **Minting**.

To mint some tokens:

```bash
$ spl-token mint BigWcBZAgDUTY2XpDYn46DPUSKDJuJ4mG9LYiDKuBjWh 1000 --url devnet
Minting 1000 tokens

Token: BigWcBZAgDUTY2XpDYn46DPUSKDJuJ4mG9LYiDKuBjWh
Recipient: 4RQQyBadpcr....7Efwy

$ spl-token balance BigWcBZAgDUTY2XpDYn46DPUSKDJuJ4mG9LYiDKuBjWh --url devnet
1000
```

##  **Checking the Circulating Amount of your Token**

The circulating supply of a token refers to the total number of tokens that are being used by Solana users. To check the circulating amount of your token:

```bash
$ spl-token supply BigWcBZAgDUTY2XpDYn46DPUSKDJuJ4mG9LYiDKuBjWh --url devnet
1000
```

It makes since we have minted 1000 tokens.

You have the ability to mint unlimited amount of tokens, but it is not ideal to have that ability.

For example, you have a project and invited the investors to give them some percentage of ownership of that project. Usually by contract, the percentage should not drop but since you have the ability to mint unlimited tokens you can drop the percentage of ownership.

To disable minting tokens:

```bash
$ spl-token authorize BigWcBZAgDUTY2XpDYn46DPUSKDJuJ4mG9LYiDKuBjWh mint --disable --url devnet

Updating BigWcBZAgDUTY2XpDYn46DPUSKDJuJ4mG9LYiDKuBjWh
    Current mint authority: ...
    New mint authority: disabled


Signature: Signature: T2m3192ZqKa2...231aBxR2qAggz
```

When you try to mint new tokens you will get an error. 

> Warning: Once minting token is disabled, it cannot be re-enabled again.

You can also burn some tokens that is minted to the token account. This operation will not burn the tokens owned by other Solana users.

To burn some tokens: 

```bash
$ spl-token burn 4RQQyBadpcr....7Efwy 100 --url devnet
Burn 100 tokens
    Source: 4RQQyBadpcr....7Efwy

Signature: 44gYKchKSJMdfO1B...7ZRXubWoBOyGdoZ1n

$ spl-token balance BigWcBZAgDUTY2XpDYn46DPUSKDJuJ4mG9LYiDKuBjWh --url devnet
900
```

## **Transfering Minted Token to Another Wallet**

In order to distribute the token you need to transfer minted token to a specific wallet address. To transfer some minted token:

```bash
$ spl-token transfer BigWcBZAgDUTY2XpDYn46DPUSKDJuJ4mG9LYiDKuBjWh 150 HAkTRWkUMcPYisqvDSqzeeGaZsLuV7WvcX7eYYkaQZ1z --url devnet --allow-unfunded-recipient --fund-recipient
```

> Warning: Before transfering the tokens, if the recipient does not add the token mint address to his wallet, he will not see the transferred tokens.

