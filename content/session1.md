📝 Session 1 Summary

📌1. OFF-CHAIN VS ON-CHAIN CODE:
- Off-chain Transactions:
    These happen outside the blockchain, making them faster and cheaper. However, they rely on other systems to ensure correctness. Off-chain code typically handles transaction creation, signing, and submission.

    Common off-chain tools:
    - cardano-cli
    - lucid (TypeScript/JavaScript)
    - mesh sdk (TypeScript/JavaScript)
    - pycardano (Python)
    - cardano-serialization-lib (JavaScript/WebAssembly)
    - atlas (Haskell)
    - plutus Application Backend (PAB)

    Example: Using a payment channel like Hydra to process transactions quickly off-chain, then settling the final result on-chain.
    Off-chain Code Example (Plutus with PAB):
    paySeller :: Contract w s Text ()
    paySeller = do
        let tx = mustPayToPubKey sellerPubKeyHash (lovelaceValueOf 1000000)
        void (submitTx tx)
    This code runs off-chain to build and submit the transaction, interacting with the on-chain script.

- On-chain Transactions:
    These happen directly on the blockchain. They offer high security and transparency, but can be slower and more expensive due to network validation. On-chain code usually enforces the rules of smart contracts.

    Common on-chain tools:
    - alken (Rust)
    - opshin (Python)
    - plutus-tx (Haskell)
    - helios (JavaScript/TypeScript)
    - plu-ts (TypeScript)

    Example: Buying an NFT directly on the Cardano blockchain requires on-chain validation, ensuring transparency but taking time and costing fees.
    On-chain Code Example (Plutus):
    validate :: PubKeyHash -> () -> ScriptContext -> Bool
    validate seller _ ctx = txSignedBy (scriptContextTxInfo ctx) seller
    This code checks if the transaction is signed by the seller. It runs directly on the Cardano blockchain.


📌2. THE BLOCKCHAIN TRANSACTION LIFECYCLE
    1-Transaction Creation: The user creates a transaction, specifying sender, recipient, and amount.
    2-Signing: The sender signs the transaction with their private key.
    3-Broadcasting: The signed transaction is sent to the network.
    4-Validation: Nodes check the transaction’s validity (signature, balance) and place it in the mempool.
    5-Inclusion in a Block: A validator/miner adds the transaction to a new block.
    6-Consensus: Nodes agree on the new block, ensuring all transactions are valid.
    7-Block Addition: The block is added to the blockchain, confirming the transaction.
    8-Finality: After a few more blocks, the transaction is considered final and irreversible.    


📌3. HASHFUNCTION, Asymmetric Encryption, and Digital Signatures
- Hash Functions: A function that transforms input data into a fixed-length string of characters, known as the "hash value." Popular hash functions like SHA-256 ensure that even a small change in the input results in a completely different hash value.
    Example: If you input "Hello" into a hash function, it might produce "5d41402abc4b2a76b9719d911017c592." But if you change it to "hello," the result would be completely different.

-  Asymmetric Encryption: Uses two keys: a public key and a private key. The public key is used to encrypt data, while the private key is used to decrypt it. This mechanism ensures both security and authenticity in transactions.
    Example: Alice encrypts a message with Bob’s public key. Only Bob can decrypt it using his private key.

- Digital Signatures: A code created by encrypting data with a private key. Digital signatures verify the sender's identity and ensure data integrity.
    Example: Alice signs a transaction with her private key, and anyone can verify the signature using her public key.


📌4. WALLET & ADDRESSES
- Wallet: A tool that manages public and private keys, enabling users to create and sign transactions on the blockchain.
    Example: A Cardano wallet like Yoroi or Daedalus manages your keys and helps you send ADA.

- Address: A string of characters representing a location for receiving assets on the blockchain. Wallet addresses are derived from public keys and help track assets.
    Example: Bob shares his wallet address with Alic e so she can send him ADA.


📌5. UTXO MODEL and SMART CONTRACTS
- UTxO Model (Unspent Transaction Output): This model tracks account balances through "unspent transaction outputs." When a transaction is made, the old outputs are consumed, and new outputs are created, ensuring transparency and immutability.
    Example: If Alice has 10 ADA and sends 3 ADA to Bob, the transaction will create two outputs: 3 ADA to Bob and 7 ADA back to Alice as change.

- Smart Contracts: Self-executing code that automatically performs actions when specific conditions are met. On Cardano, smart contracts are written in Plutus, enabling secure and complex transaction logic.
    Example: A smart contract automatically releases payment to a seller once the buyer confirms delivery.