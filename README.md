
# 1-Click Ethereum Sepolia Node + Custom Aztec RPC
**Powered by Noderhunterz**

This repo provides a fully automated, one-click script to launch your own full Ethereum Sepolia node using **Geth** (execution client) and **Prysm** (consensus client), with a **custom RPC endpoint** for use with the Aztec network.

---

## Features

- One-click setup for Geth + Prysm via Docker
- Custom RPC endpoint for Aztec CLI or Sequencer
- Full Sepolia node support
- Secure JWT secret generation
- Automatic dependency and Docker installation
- Ideal for developers and node runners

---

## Quick Start

```bash
sudo apt-get -qq update && sudo apt-get upgrade -y
sudo apt -qq install curl -y
```
```bash
curl -s https://raw.githubusercontent.com/codedialect/geth-prysm-rpc-node/main/setup_geth_prysm.sh  | sudo bash
```

---

## What It Sets Up

- `/root/ethereum/execution` Geth data directory  
- `/root/ethereum/consensus`  Prysm data directory  
- `/root/ethereum/jwt.hex`  JWT secret used by both clients  
- Docker services:
  - **Geth** (Ethereum Sepolia full node)
  - **Prysm** (Beacon/Consensus client)

---

## Aztec RPC Endpoints

- **Execution Layer (Geth)**  
  `http://<your-vps-ip>:8545`

- **Consensus Layer (Prysm)**  
  `http://<your-vps-ip>:3500`

Use these with Aztec CLI or Sequencer configurations.

---

## Recommended Firewall Rules

```bash
# Allow P2P for geth
sudo ufw allow ssh
sudo ufw allow 22
sudo ufw allow 30303/tcp
sudo ufw allow 30303/udp

# Allow local access for RPCs (If you want to use the RPCs in the same vps)
sudo ufw allow from 127.0.0.1 to any port 8545 proto tcp
sudo ufw allow from 127.0.0.1 to any port 3500 proto tcp

# Allow specific vps access for RPCs (If you want to use the RPCs in the specific vps)
sudo ufw allow from <your_ip> to any port 8545 proto tcp
sudo ufw allow from <your_ip> to any port 3500 proto tcp

# Allow to run any remote vps
sudo ufw allow 8545/tcp
sudo ufw allow 3500/tcp
```

---

## Sync Status Checks

**Check Geth sync:**
```bash
curl -X POST -H "Content-Type: application/json" \
--data '{"jsonrpc":"2.0","method":"eth_syncing","params":[],"id":1}' \
http://localhost:8545
```

**Check Prysm sync:**
```bash
curl http://localhost:3500/eth/v1/node/syncing
```

**Check logs:**
For prysm logs:
```bash
sudo docker logs prysm -fn 100
```

For Consensus(geth) logs:
```bash
sudo docker logs geth -fn 100
```
---

## Contributing

Got ideas, scripts, or improvements? PRs are welcome!  
Join us in pushing decentralization forward

---

## Community & Support

Discord: [coming soon] 

---
