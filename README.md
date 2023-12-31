# Concordia: A Protocol Enabling Trustless Atomic Swaps of Digital Deliverables

**Abstract**. The Concordia protocol is a versatile and decentralized solution that facilitates irrevocable atomic exchanges of digital work for cryptocurrency. This protocol addresses the inherent challenges of trust and security in online collaborations, providing a transformative approach to enhance trust, transparency, and efficiency in digital work exchanges. By establishing clear conditions and utilizing cryptographic techniques, Concordia fosters a more equitable and harmonious environment for all parties involved.

## 1. Introduction

The workforce landscape has been significantly shaped by the internet and globalization, offering flexibility and autonomy in employment opportunities. However, this new model of work presents challenges in establishing trust and ensuring security between individuals collaborating online, often located in different jurisdictions. Contractors face payment security risks, while clients have concerns about making advance payments without receiving the work.

To address these challenges, a highly-configurable and decentralized intermediary is needed to enable trustless atomic transfers of digital deliverables between two consenting parties. This intermediary establishes conditions prior to delivery, mitigating risks for both parties and ensuring the integrity and finality of each exchange.

## 2. Architecture

The Concordia protocol consists of multiple components within a single "instance." These components include an ECDSA (Elliptic Curve Digital Signature Algorithm) key pair, a smart contract deployed on a peer-to-peer (p2p) network, a decentralized p2p datastore, and a specialized "decryption oracle" with the capability to read from the datastore and write to the contract. The contract exposes a public key for transparency, while the private key remains securely accessible only to the oracle.

To handle scenarios such as key exposure or network scaling adjustments, a proxy contract can be utilized. This proxy contract allows for the creation and retirement of instances as needed, providing enhanced control over the network.

## 3. System Overview

The Concordia protocol follows a three-stage procedure for each exchange: (1) delivering an encrypted deliverable, (2) securing payment, and (3) decrypting the deliverable. Through a combination of cryptographic techniques and blockchain technology, the protocol safeguards the interests of both parties.

3.1 Deliverable Encryption (Creating a Concord)

During the initial setup, the proprietor generates an encrypted version of the original deliverable (`w`), resulting in `w_k`. This encryption process employs the Advanced Encryption Standard (AES) and a unique secret key (`k`). The secret key is further encrypted using the public key provided by the contract, ensuring its secrecy on a public ledger. The encrypted file is then securely uploaded to the InterPlanetary File System (IPFS), assigned a unique content identifier (CID).

A proof (`c`) is generated by hashing `w` and `k` independently, combining the hashes into a single byte array, and applying the keccak256 hash function.

Finally, a transaction is initiated, including `k_p`, `c`, and `CID`, creating a "Concord" on-chain.

3.2 Payment

Upon receiving full payment, an oracle is provided with `CID` and `k_p`. The oracle fetches `w_k` from IPFS using `CID` and decodes `k_p` to retrieve `k`. The decrypted `w_k` yields the original deliverable `w`.

The oracle computes the hash of `w` and `k`, combines them into a byte array, and applies the keccak256 hash function. If the resulting hash matches `c`, the key is verified as valid, and the payment becomes available for the proprietor to withdraw.

3.3 Delivery (Decrypting a Deliverable)

With the completion of the above stages, the buyer uses the key `k` to decrypt `w_k`, accessing the original deliverable, `w`.

## 4. Quality Assurance

Clients may have concerns about paying for encrypted work. Proprietors utilizing the Concordia protocol are encouraged to continue demonstrating their work to clients, similar to traditional settings. By proving that the showcased work matches the encrypted version stored on the decentralized file store, proprietors can instill confidence in the deliverables.

Additional methods can be employed to further automate or enhance confidence in the delivered work:

4.1 AI-Powered Verification: AI algorithms can be utilized to verify the integrity and quality of deliverables, recognizing specific patterns or parameters relevant to each work type.

4.2 Appointed Human Verifiers: Human verifiers can be involved in the quality assurance process, performing audits of the work and providing approval before finalization.

4.3 Partially Obfuscated Previews: Concordia incorporates a partially obfuscated preview mechanism, allowing buyers to access a part of the deliverable before making the final payment without revealing the entire content. This process ensures security and builds confidence in the work.

## 5. Conclusion

The Concordia protocol presents a comprehensive and secure solution to the challenges of trust and security in online collaboration. By leveraging blockchain technology, cryptographic operations, and third-party validation, Concordia facilitates trustless atomic swaps of digital work. With its ability to establish clear conditions, provide transparent encryption and decryption processes, and incorporate quality assurance measures, Concordia enhances trust, transparency, and efficiency in digital work exchanges. By adopting Concordia, parties can experience a more equitable and harmonious collaboration ecosystem, where risks are mitigated, and the integrity of exchanges is upheld.
