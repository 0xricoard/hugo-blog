---
title: 'MUN Nodes State-Sync'
date: Sun, 09 Oct 2022 21:44:48 +0000
draft: false
tags: ['Node Guides']
cover:
    image: "https://guides.bimasaktivalidator.my.id/wp-content/uploads/2022/10/28F9B0FA-FB84-4B23-A837-F7CAFB78095D-1024x341.jpeg"
relative: true
---

![](https://guides.bimasaktivalidator.my.id/wp-content/uploads/2022/10/28F9B0FA-FB84-4B23-A837-F7CAFB78095D-1024x341.jpeg)

For a tutorial on how to install MUN node [click here](https://github.com/elangrr/testnet_guide/tree/main/mun).

For chain id testmun

Set RPC to BimaSakti

```
RPC="http://bimasaktimunrpc.westeurope.cloudapp.azure.com:26657"
```

set variables $LATEST\_HEIGHT $BLOCK\_HEIGHT $TRUST\_HASH

```
LATEST_HEIGHT=$(curl -s $RPC/block | jq -r .result.block.header.height); \
BLOCK_HEIGHT=$((LATEST_HEIGHT - 2000)); \
TRUST_HASH=$(curl -s "$RPC/block?height=$BLOCK_HEIGHT" | jq -r .result.block_id.hash)
```

Configure persisten peers

```
peers="e1733d60e1bbbee3241f62c10257555efb8398a5@bimasaktimunrpc.westeurope.cloudapp.azure.com:26656"
sed -i.bak -e "s/^persistent_peers *=.*/persistent_peers = \"$peers\"/" $HOME/.mun/config/config.toml
```

Then copy this command

```
sed -i.bak -E "s|^(enable[[:space:]]+=[[:space:]]+).*$|\1true| ; \
s|^(rpc_servers[[:space:]]+=[[:space:]]+).*$|\1\"$RPC,$RPC\"| ; \
s|^(trust_height[[:space:]]+=[[:space:]]+).*$|\1$BLOCK_HEIGHT| ; \
s|^(trust_hash[[:space:]]+=[[:space:]]+).*$|\1\"$TRUST_HASH\"| ; \
s|^(seeds[[:space:]]+=[[:space:]]+).*$|\1\"\"|" $HOME/.mun/config/config.toml
```

Stop and reset the node

```
sudo systemctl stop mund && mund tendermint unsafe-reset-all --home $HOME/.mun --keep-addr-book
```

Start node and check logs

```
sudo systemctl restart mund && sudo journalctl -u mund -f -o cat
```
