## BitcoinDiamond three-node private network in regtest mode

- Node Pool
  - RPC Port 16101, Username: user, Password: pass
- Node Bob
  - RPC Port 16102, Username: user, Password: pass
- Node Alice
  - RPC Port 16103, Username: user, Password: pass

### build image
```bash
docker build -t bcd_private_net bcd_private_testnet/
```

### run image with internal ports exposed at host
```bash
docker run -it -d -p 16101:16101 -p 16102:16102 -p 16103:16103 bcd_private_net
```

### cli
```bash
docker exec -it <container_id> /usr/local/bin/bitcoindiamond-cli -datadir=/data/node-pool getblockchaininfo
```

### rpc:
```bash
curl --user user:pass --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "getblockchaininfo", "params": [] }' -H 'content-type: application/json;' http://127.0.0.1:16101/
```
