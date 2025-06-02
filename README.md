# Stellar Final - Atomic Swap Smart Contract

## ✨ Overview

This is a smart contract written in **Rust** using **Soroban SDK v22.0.1**, designed to perform **atomic swaps** between two users on the **Stellar Testnet**. It includes additional **admin-level freeze/unfreeze** account control features to manage malicious behavior.

Contract is fully compatible with **Soroban Protocol 22** and was deployed using **stellar-cli v22.0.1**.

---

## 📈 Features

### 🔄 Atomic Swap

* Secure token exchange between two users.
* Minimum amount constraints on both sides.
* If conditions aren't met, the swap is reverted.
* All-or-nothing execution (atomicity).

### 🧪 Freeze / 🔓 Unfreeze

* Admin can freeze accounts to disable token transfers.
* Frozen accounts cannot participate in swaps.
* Only admin can unfreeze.

### 🔐 Admin Role

* Admin address is stored in contract state.
* Freeze and unfreeze actions are restricted to the admin only.

---

## 🛠️ Tools & Stack

* **Rust 1.84.0**
* **Soroban SDK 22.0.1**
* **stellar-cli 22.0.1** (`cargo install --locked stellar-cli --version 22.0.1`)
* Target: `wasm32-unknown-unknown`
* Network: **Stellar Testnet**

---

## 🚀 Compilation & Deployment Steps

### ✅ 1. Install WASM target:

```bash
rustup target add wasm32-unknown-unknown
```

### ✅ 2. Build the contract:

```bash
cargo build --release --target wasm32-unknown-unknown
```

### ✅ 3. Generate and fund a keypair:

```bash
soroban keys generate --global fatih --network testnet --fund
```

Then:

```bash
soroban keys address fatih     # Public
soroban keys show fatih        # Secret
```

Export them:

```bash
export SOROBAN_SECRET_KEY=SDAOBIBWN44TPXUFPESU6DMUOBV6KTFBXCG4EZEKNFXPIKWXMP5OQANS
export SOROBAN_ADDRESS=GCPRCHFGXM7DLAF6W5JNZVU3SRD3GW3BZ4DCNGP4FYCG2BYOEJ2F7QV7
```

### ✅ 4. Deploy to Testnet:

```bash
soroban contract deploy \
  --source $SOROBAN_SECRET_KEY \
  --network testnet \
  --rpc-url https://soroban-testnet.stellar.org \
  --network-passphrase "Test SDF Network ; September 2015" \
  --wasm target/wasm32-unknown-unknown/release/stellar_final_contract.wasm
```

### 🔍 Deployment Confirmation:

```
✅ Deployed!
Contract ID: CBJERT7UZUQIEWYMINQULFQI3A3G4I6C74LJTDU6EZZ2LITXHPKXTFUX
Transaction: https://stellar.expert/explorer/testnet/tx/3779f2f037d1a14f1f6397c8234fc687ec9513aad0807fc89e3ffcb12d639235
Contract: https://stellar.expert/explorer/testnet/contract/CBJERT7UZUQIEWYMINQULFQI3A3G4I6C74LJTDU6EZZ2LITXHPKXTFUX
```

---

## 🔢 Contract Behavior

1. Admin deploys contract.
2. Two users submit swap requests with token and conditions.
3. Tokens get transferred to contract.
4. If both sides match expected values, swap succeeds.
5. If either account is frozen, contract aborts.
6. Admin can freeze/unfreeze specific addresses.

---

## 🖊️ License

MIT

---

> This contract and deployment process were built during the **Stellar Fullstack Bootcamp**, demonstrating secure and compliant atomic swap functionality on the Soroban protocol.
