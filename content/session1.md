Session 1 Summary

1. Understanding Hash Functions, Asymmetric Encryption, and Digital Signatures

- Hash Functions: A function that transforms input data into a fixed-length string of characters, known as the "hash value." Popular hash functions like SHA-256 ensure that even a small change in the input results in a completely different hash value.

Asymmetric Encryption: Uses two keys: a public key and a private key. The public key is used to encrypt data, while the private key is used to decrypt it. This mechanism ensures both security and authenticity in transactions.

Digital Signatures: A code created by encrypting data with a private key. Digital signatures verify the sender's identity and ensure data integrity.

2. Distinguishing Wallets and Addresses

Wallet: A tool that manages public and private keys, enabling users to create and sign transactions on the blockchain.

Address: A string of characters representing a location for receiving assets on the blockchain. Wallet addresses are derived from public keys and help track assets.

3. Understanding the UTxO Model and Smart Contracts

UTxO Model (Unspent Transaction Output): This model tracks account balances through "unspent transaction outputs." When a transaction is made, the old outputs are consumed, and new outputs are created, ensuring transparency and immutability.

Smart Contracts: Self-executing code that automatically performs actions when specific conditions are met. On Cardano, smart contracts are written in Plutus, enabling secure and complex transaction logic.