
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
   - Go to the Microsoft Store and search for "Ubuntu" (or any other preferred Linux distribution).
   - Click "Get" and install it.
  
6. **Set Up Your Linux Distribution:**:
   - Once installed, launch it from the Start menu.
   - The first launch will take some time as it completes installation.
   - Set your UNIX username and password when prompted.

### 2. Set Up Solana Tools

After installing WSL, install the Solana tools.

#### Steps:
1. Open your Linux distribution via the start menu.
2. Update your package lists:
   ```bash
   sudo apt update
   ```
3. Install Solana's CLI tools:
   ```bash
   sh -c "$(curl -sSfL https://release.solana.com/v1.18.4/install)"
   ```

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
