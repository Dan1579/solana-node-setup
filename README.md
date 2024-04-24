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

#### Steps:
1. Open PowerShell as Administrator:
   - Search for PowerShell in the Start menu, right-click on it, and select "Run as administrator".

2. Enable the Windows Subsystem for Linux:
   ```powershell
   wsl --install
