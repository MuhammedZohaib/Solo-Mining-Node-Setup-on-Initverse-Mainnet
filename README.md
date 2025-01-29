# Solo Mining Node Setup on Initverse Mainnet

## Introduction
This guide will walk you through setting up a solo mining node on the **Initverse Mainnet**. This process requires a **Linux environment** such as **WSL (Windows Subsystem for Linux)** or a **Linux VPS**.

## Prerequisites
Before proceeding, ensure you have access to a Linux-based system:
- **WSL (Windows Subsystem for Linux)** if using Windows
- **A Linux VPS** (Ubuntu/Debian recommended)
- **A dedicated Linux machine**

### Install Dependencies
Ensure you have **Go** and **Make** installed. If they are not installed, run the following command:
```sh
sudo apt update && sudo apt install make golang-go
```

## Clone the Repository
Download the Initverse chain repository from GitHub:
```sh
git clone https://github.com/Project-InitVerse/chain.git
cd chain
```

## Build Geth
Compile the Geth (Go Ethereum) binary:
```sh
make geth
```

## Run Initverse Mainnet Node
After building Geth, start your node with the following command:
```sh
sudo ./build/bin/geth --datadir data --http --syncmode full console --ipcpath /tmp/geth.ipc
```
### Expected Output
If successful, you will see blockchain synchronization messages. This process may take some time.

## Mining Setup
Once synchronization is complete, configure mining by setting your **Ethereum wallet address**:
```sh
miner.setEtherbase('your_mainnet_address_here')
```
Start mining with:
```sh
miner.start()
```
To mine with **3 threads**:
```sh
miner.start(3)
```
To stop mining:
```sh
miner.stop()
```

## Checking Synchronization Status
To check if your blockchain is synchronizing, use:
```sh
eth.syncing
```
If synchronization is complete, this command will return `false`.

## Additional Tips
- Ensure your **VPS has sufficient CPU and RAM** to handle mining operations.
- If using **WSL**, allow external connections via firewall settings.
- You can run the node in the background using `screen` or `tmux` to keep it active after closing the terminal.

## Support & Credits
If you found this repository useful, please **star** the repo!

Developed by **Muhammad Zohaib**
