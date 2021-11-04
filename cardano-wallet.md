
## How to install and use cardano-wallet

Most of this information is coming from the offical documentation of `cardano-wallet`
https://github.com/input-output-hk/cardano-wallet/wiki

But I summarized it here

```
mkdir -p $HOME/cardano-src
cd $HOME/cardano-src
git clone https://github.com/input-output-hk/cardano-wallet.git --depth=1
cd cardano-wallet
git fetch --all --recurse-submodules --tags --depth=1
git checkout tags/v2021-09-29
cabal configure --with-compiler=ghc-8.10.4
cabal build all
mkdir -p ~/.local/bin
cp -p "dist-newstyle/build/x86_64-linux/ghc-8.10.4/cardano-wallet-2021.9.29/no-wallet/build/cardano-wallet/cardano-wallet" $HOME/.local/bin/
cardano-wallet version
vi ~/.bashrc # Edit path to include ~/.local/bin/
source ~/.bashrc
cardano-wallet vcd $CNODmkdir cd w
echo cardano-wallet serve --node-socket $CARDANO_NODE_SOCKET_PATH --database /opt/cardano/cnode/wallet/db --listen-address 0.0.0.0 --testnet
```

Run the wallet 
```
cardano-wallet serve --node-socket $CARDANO_NODE_SOCKET_PATH --database $CNODE_HOME/wallet/wallets-testnet --listen-address 0.0.0.0 --testnet $CNODE_HOME/files/byron-genesis.json --port 8091

# mainnet
cardano-wallet serve --node-socket $CARDANO_NODE_SOCKET_PATH --database /opt/cardano/cnode/wallet/wallets-mainnet --listen-address 0.0.0.0 --mainnet --port 8090

```



Create a new wallet

```
cardano-wallet recovery-phrase generate

cardano-wallet wallet create from-recovery-phrase wallet-1

wal = Wallet("<wallet-id>", backend=WalletREST(port=8090))


```