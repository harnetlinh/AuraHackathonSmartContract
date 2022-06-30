# Information
> **Address Owner**: 
> aura1dzmkendynq73t0jvcj24s8t0dnexuj07x6juws

> **Address smart contract**: aura16vm6ex9yp8jvp0f6vua2kfmsw04wh24lvt3l6xq62gj97u9c9hnswywk32

> **Mnemonic**: eagle melody aim spatial raise crane kit catch hobby crane vapor thumb cat mandate day dentist cruise rubber object annual best tiger swear angry

# Env
- **Go**
- **Rust**
- **jq**
- **Aura Daemon**
# Command to deploy
## Install Wasm32
```
rustup target add wasm32-unknown-unknown
```
## Build smart contract
```
cd ./contract/cw721-base
rustup default stable
RUSTFLAGS='-C link-arg=-s' cargo wasm
```

## Deploy smart contract
```
aurad tx wasm store  ../../target/wasm32-unknown-unknown/release/cw721_base.wasm --from wallet --node https://rpc.serenity.aura.network:443 --chain-id serenity-testnet-001 --gas-prices 0.025uaura --gas auto --gas-adjustment 1.3
```

- Get CODE_ID of smart contract in https://serenity.aurascan.io/ with hash code in above command

## Init smart contract
```
aurad tx wasm instantiate ${CODE_ID} '{"minter":"${ADDRESS_OWNER}","name":"Aura NFT","symbol":"ANFT"}' --from wallet --label "cw721" --node https://rpc.serenity.aura.network:443 --chain-id serenity-testnet-001 --gas-prices 0.025uaura --gas auto --gas-adjustment 1.3 -y --no-admin
```
