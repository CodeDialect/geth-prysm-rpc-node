
# ðŸš€ 1-Click Ethereum Sepolia Node + Custom Aztec RPC
**Powered by Noderhunterz**

This repo provides a fully automated, one-click script to launch your own full Ethereum Sepolia node using **Geth** (execution client) and **Prysm** (consensus client), with a **custom RPC endpoint** for use with the Aztec network.

---

## ðŸ”§ Features

- âœ… One-click setup for Geth + Prysm via Docker
- âœ… Custom RPC endpoint for Aztec CLI or Sequencer
- âœ… Full Sepolia node support
- âœ… Secure JWT secret generation
- âœ… Automatic dependency and Docker installation
- âœ… Ideal for developers and node runners

---

## âš¡ï¸ Quick Start

```bash
curl -s https://raw.githubusercontent.com/noderhunterz/geth-prysm-aztec-rpc/main/setup-geth-prysm.sh | sudo bash
```

> âš ï¸ Script is designed for Ubuntu 20.04 or newer. Must be run as root or with `sudo`.

---

## ðŸ“‚ What It Sets Up

- `/root/ethereum/execution` â†’ Geth data directory  
- `/root/ethereum/consensus` â†’ Prysm data directory  
- `/root/ethereum/jwt.hex` â†’ JWT secret used by both clients  
- Docker services:
  - **Geth** (Ethereum Sepolia full node)
  - **Prysm** (Beacon/Consensus client)

---

## ðŸ§ª Aztec RPC Endpoints

- **Execution Layer (Geth)**  
  `http://<your-vps-ip>:8545`

- **Consensus Layer (Prysm)**  
  `http://<your-vps-ip>:3500`

Use these with Aztec CLI or Sequencer configurations.

---

## ðŸ“º Watch the Full Walkthrough

[![YouTube Thumbnail](https://github.com/noderhunterz/assets/blob/main/aztec-rpc-thumb.png)](https://youtube.com/your-video-link)

---

## ðŸ”’ Recommended Firewall Rules

```bash
# Allow P2P for geth
sudo ufw allow 30303/tcp
sudo ufw allow 30303/udp

# Allow local access for RPCs
sudo ufw allow from 127.0.0.1 to any port 8545 proto tcp
sudo ufw allow from 127.0.0.1 to any port 3500 proto tcp
```

---

## ðŸ“¡ Sync Status Checks

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

## ðŸ‘¨â€ðŸ’» Contributing

Got ideas, scripts, or improvements? PRs are welcome!  
Join us in pushing decentralization forward ðŸ’¥

---

## ðŸ§  Credits

Created by **Noderhunterz**  
Inspired by the [Aztec Sequencer Docs](https://github.com/AztecProtocol/aztec-packages)  
Base Geth/Prysm setup adapted from community best practices.

---

## ðŸ’¬ Community & Support

ðŸ—¨ï¸ Discord: [coming soon]  
ðŸ¦ Twitter: [@noderhunterz](https://twitter.com/noderhunterz)

---

## ðŸª™ Donations

If this saves you time, consider tipping in ETH:

`0xYourDonationWalletAddressHere`

â¤ï¸ Stay decentralized!
