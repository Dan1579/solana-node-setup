## Test Accommodation for Airdrop Wallet

#### Configure Solana CLI

Now that Solana CLI is installed, you can configure it to connect to a specific network. For development purposes, connecting to the Devnet is recommended as it allows you to work with test SOL without real-world value.

1. **Configure to Devnet**:
   - Ensure that your Solana CLI is configured to connect to the Devnet by running:
     ```bash
     solana config set --url https://api.devnet.solana.com
     ```

2. **Generate a New Wallet**:
   - If you don't already have a wallet, you can create one using Solana CLI. This wallet will be used to receive and send SOL on the Devnet.
   - Run the following command to create a new wallet. Make sure to note down your seed phrase and keep it in a secure location:
     ```bash
     solana-keygen new
     ```

3. **Request an Airdrop**:
   - Since you're working on Devnet, you can request test SOL through an airdrop. This is useful for development and testing without needing to use real funds.
   - Use the `solana airdrop` command to request free test SOL. Replace `<AMOUNT>` with the number of SOL you wish to receive and `<YOUR_WALLET_ADDRESS>` with your wallet's public address:
     ```bash
     solana airdrop <AMOUNT> <YOUR_WALLET_ADDRESS>
     ```
   - For example, to request 1 test SOL to your wallet:
     ```bash
     solana airdrop 1 FAXHGQoiGyqoHMTLnf2eUn5meo47g56miQxfUajo6udU
     ```

4. **Check Wallet Balance**:
   - After receiving the airdrop, it's a good practice to check your wallet's balance to ensure the test SOL has been credited.
   - Verify the amount of SOL in your wallet by running:
     ```bash
     solana balance
     ```

5. **Ping the Network**:
   - After setting up your node and verifying your wallet's balance with the airdropped SOL, it is useful to test the network connectivity and response times of your node. This helps ensure that your setup is properly communicating with the Solana network.
   - Use the `solana ping` command to send 5 test transactions to the network. This command measures the round-trip time for each transaction:
     ```bash
     solana ping -c 5
     ```
   - This will output the time taken for each ping transaction, giving you an insight into the performance and stability of your connection to the Solana network.
