# crypto wallet

## Research question

How does wallets such as metamask and trust wallet work?
Dissecting the system architecture and everything that is involved
in the creation of a Blockchain wallet infrastructure.

## Parts
1. UI and Cross-Platform Availability
2. Wallet Creation and Management
3. Transaction Management
4. Blockchain Interaction
5. Security and Privacy
6. Network and Token Support
7. Extensions and Integration

### Wallet Creation and Management
1. When user signs up on UI, wallet is created. Key generation and storage for user occurs. 
This is done with ECDSA cryptography on Ethereum blockchain, 
but a client like Geth can handle that.

2. Like Metamask and co, generate a seed phrase (maybe 12 or 24 word mnemonic seed phrase). 
To avoid collision and to enable the ability to retrieve it if it is forgotten, 
then derive it using the user's private key or password, using BIP39 standards.

3. Encrypt the seed phrase using AES-256-CBC. Store in the platform of choice. 
I don't think it's safe to store in the mobile application. Ask Seb Hendrix about this.

### Transaction Management
1. Should be easy to use a real Ethereum address and a client like Geth to create transactions.

2. Transactions have 3 parts on Ethereum:
- initialize the txn
- sign the txn
- broadcast the txn on Ethereum

3. Implement using Geth client.

4. Find link from Infura, maybe. I believe a project of this scale should run a full node locally
to have a level of control etc.

5. To interact with dApps (technically just smart contracts on the network), requires more thinking.

### Security and Privacy
1. Not including the user's name, email, password, etc in the transaction process. Kind of pseudonymous.
2. Metro mentioned a one-way encryption algorithm (PK something). Research and implement it 
for platform storage of the private key. Implement HashAndCompareHash function to be used during login.

### Network and Token Support
1. Multi-network support would be wild, but just a repetition of this process above.
Get a client, get a node, interface with it.
2. Token management can work same way as Metamask. 
Ask for token details and the network it belongs to.
Fetch it from the network, and it should work. 
Creating User addresses would probably depend on the network.

### Extensions and Integration
1. Wallets can be integrated into other dApps, exchanges, etc.
Would be solved easily if the wallet is a dApp or a local application.