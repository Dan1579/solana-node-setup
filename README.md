# Solana Node Setup on Windows

This repository documents the setup and configuration of a Solana node running under Windows 11 using WSL (Windows Subsystem for Linux).

## Prerequisites

Before starting, ensure your system meets the following prerequisites:
- Windows 11 Pro 64-bit
- WSL enabled
- Node.js installed (if running custom Node.js scripts)

## Installation Steps

### 1. Install Windows Subsystem for Linux (WSL)

To run Solana on Windows, WSL must be installed to provide a Linux-based environment.

#### Steps to Enable WSL and Virtual Machine Platform:

1. **Open PowerShell as Administrator**:
   - Search for PowerShell in your Start menu, right-click on it, and select "Run as administrator".

2. **Enable the WSL Feature**:
   - In the PowerShell window, type the following command and press Enter:
     ```shell
     dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
     ```

3. **Enable Virtual Machine Platform**:
   - Still in PowerShell, type the following command and press Enter:
     ```shell
     dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
     ```

4. **Restart Your Computer**:
   - Restart your computer to apply the changes.
    
5. **Install a Linux Distribution from the Microsoft Store**:
   - Go to the Microsoft Store and search for "Ubuntu" (Ubuntu 22.04.3 LTS) (or any other preferred Linux distribution).
   - Click "Get" and install it.
  
6. **Set Up Your Linux Distribution:**:
   - Once installed, launch it from the Start menu.
   - The first launch will take some time as it completes installation.
   - Set your UNIX username and password when prompted.

### 2. Set Up Solana Tools

With WSL and Linux ready, you can install the Solana tools.

#### Steps:
1. **Update your Linux packages**
   - Open your Linux terminal (Ubuntu or chosen distro) and run:
   ```bash
   sudo apt update && sudo apt upgrade
   ```
2. **Install Solana CLI Using the Provided Command**:
   - Since the [documentation](https://docs.solanalabs.com/cli/install) provides a specific version, let's install that. You can use the command for installing the Solana release v1.18.4 (or replace it with any other version number if needed). Run this in your Linux terminal:
   ```bash
   sh -c "$(curl -sSfL https://release.solana.com/v1.18.4/install)"
   ```
   This command will download and install the specified version of Solana CLI.
   
3. **Update Your PATH**:
   - If the installer prompts you to update your PATH, follow the instructions provided. Usually, it will suggest a command that you should run, something similar to:
   ```bash
   echo 'export PATH="$HOME/.local/share/solana/install/active_release/bin:$PATH"' >> ~/.bashrc
   ```
   - After running the suggested command, apply the changes with:
   ```bash
   source ~/.bashrc
   ```
4. **Verify Solana Installation**:
Confirm that Solana CLI has been installed correctly:
   - Run:
     ```bash
     solana --version
     ```
     This should display the installed version of Solana CLI.

## Optional Features

For users interested in testing and experimenting with Solana CLI, please refer to the following guides:

- [Test Accommodation for Airdrop Wallet](./test-accommodation-guide.md): Detailed instructions for setting up a wallet, receiving airdrops, and testing wallet functionality on the Solana Devnet.

- [Appendix: Advanced Solana CLI Interactions](./advanced-cli-interactions.md): A comprehensive guide on advanced CLI commands for token creation, staking, and other network interactions.

### 4. Proceed with Configuration

Once Solana CLI is installed, the next steps involve configuring your node and setting up the environment for transaction monitoring and running scripts.

#### Configure the Solana Node

1. **Initialize Solana Configuration**:
   - It's important to configure your Solana node to connect to the desired network (testnet, mainnet, or devnet). Run:
     ```bash
     solana config set --url https://api.mainnet-beta.solana.com
     ```
   - This command sets the node to connect to the Solana mainnet-beta.

2. **Create a Wallet**:
   - Create a new Solana wallet, which will be used to manage funds and transactions. Run:
     ```bash
     solana-keygen new --outfile ~/.config/solana/id.json
     ```
   - This will create a new keypair and save it to the specified file. Remember to back up your seed phrase securely.

3. **Fund Your Wallet**:
   - For transaction fees and to participate in the network, you need some SOL in your wallet. Obtain SOL through a faucet if you're using testnet or purchase SOL and transfer it to the wallet address shown by:
     ```bash
     solana address
     ```

### 4. Monitoring and Script Execution

#### Set Up Node.js for Scripting

1. **Install Node.js**:
   - If not already installed, set up Node.js in your Linux environment:
     ```bash
     curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -
     sudo apt-get install -y nodejs
     ```
   - This installs Node.js, which you'll use for writing and executing scripts.

2. **Install solana/web3.js**:
   - Install the Solana JavaScript API library to interact with the Solana blockchain:
     ```bash
     npm install @solana/web3.js
     ```

#### Develop Transaction Monitoring Scripts

1. **Write Your Script**:
   - Create a new file for your monitoring script, for example, `monitor.js`.
   - Use the `@solana/web3.js` library to subscribe to transactions, check balances, or send transactions. Here’s a simple example to get started:
     ```javascript
     const web3 = require('@solana/web3.js');
     let connection = new web3.Connection(web3.clusterApiUrl('mainnet-beta'));

     async function checkBalance() {
       let wallet = new web3.PublicKey('Your-Wallet-Address-Here');
       let balance = await connection.getBalance(wallet);
       console.log(`Balance: ${balance / web3.LAMPORTS_PER_SOL} SOL`);
     }

     checkBalance();
     ```

#### Run Your Script

1. **Execute the Script**:
   - Run your monitoring script with Node.js:
     ```bash
     node monitor.js
     ```

### 5. Troubleshooting and Common Issues

1. **Common Errors**:
   - Document any common issues or errors that might occur during setup or operation and provide solutions.

2. **Support**:
   - Provide links to Solana documentation or forums for additional help.

## Conclusion

This setup guide provides the fundamental steps to get your Solana node up and running on Windows using WSL. It includes how to install necessary tools, configure your node, and begin monitoring transactions with custom scripts. For any updates, refer to the [official Solana documentation](https://docs.solanalabs.com/).
