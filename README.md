
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
curl -s https://raw.githubusercontent.com/noderhunterz/geth-prysm-aztec-rpc/main/setup-geth-prysm.sh | sudo bash
```


---

## What It Sets Up

- `/root/ethereum/execution` â†’ Geth data directory  
- `/root/ethereum/consensus` â†’ Prysm data directory  
- `/root/ethereum/jwt.hex` â†’ JWT secret used by both clients  
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

## Watch the Full Walkthrough

[![YouTube Thumbnail](https://github.com/noderhunterz/assets/blob/main/aztec-rpc-thumb.png)](https://youtube.com/your-video-link)

---

## Recommended Firewall Rules

```bash
# Allow P2P for geth
sudo ufw allow 30303/tcp
sudo ufw allow 30303/udp

# Allow local access for RPCs
sudo ufw allow from 127.0.0.1 to any port 8545 proto tcp
sudo ufw allow from 127.0.0.1 to any port 3500 proto tcp
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

---

## Contributing

Got ideas, scripts, or improvements? PRs are welcome!  
Join us in pushing decentralization forward ðŸ’¥

---

## Credits

Created by **Noderhunterz**  
Inspired by the [Aztec Sequencer Docs](https://github.com/AztecProtocol/aztec-packages)  
Base Geth/Prysm setup adapted from community best practices.

---

## Community & Support

ðŸ—¨ï¸ Discord: [coming soon]  
ðŸ¦ Twitter: [@noderhunterz](https://twitter.com/noderhunterz)

---

## Donations

If this saves you time, consider tipping in ETH:

`0xYourDonationWalletAddressHere`

Stay decentralized!
