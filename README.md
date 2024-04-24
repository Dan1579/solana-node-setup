
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


### 3. Configuration and Testing

Detail the configuration steps and how to start the Solana validator for testing.

#### Example Command:
```bash
solana-test-validator
```

## Further Development

Discuss how you plan to develop and test the calculation algorithms and transaction monitoring scripts using Node.js and `@solana/web3.js`.

## Troubleshooting

Include common issues and troubleshooting steps for setting up the Solana node.
