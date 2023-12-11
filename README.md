# Bitcoin Hash Object Protocol (BHO)

## Overview
Bitcoin Hash Object (BHO) is an experimental protocol that extends Bitcoin's functionalities. This initiative emerged from a Twitter discussion regarding [Whether "Inscription" is a Bug or Feature](https://twitter.com/jolestar/status/1732711942563959185). BHO aims to utilize these inscriptions advantageously, treating them as a feature while tackling the technical challenges they present.

## Objectives
- To delve into and understand Bitcoin's protocol intricacies.
- To thoroughly analyze existing Bitcoin extension protocols, identifying their strengths and weaknesses.
- To facilitate practical learning through hands-on protocol design.

## Key Challenges & Trade-offs

1. **UTXO Trace**: 
   - **Challenge**: Deciding on using UTXO for tracking asset transfers in extension protocols.
   - **Trade-offs**: Leveraging UTXO might increase 'dust' and bloat the Bitcoin network, while not using it could limit the verification of asset ownership and the implementation of PSBT for exchanges.

2. **Data Embedding**: 
   - **Challenge**: Determining the optimal location for data embedding in Bitcoin transactions.
   - **Trade-offs**: Embedding in the Witness section might be perceived as misuse, while using OP_RETURN foregoes the benefits of UTXO features.

3. **Asset Type**: 
   - **Challenge**: Deciding whether the protocol should cater to NFTs, FTs, or both.

4. **Extensibility**: 
   - **Challenge**: Determining the protocol's capacity for future expansion and upgrades.
   - **Trade-offs**: For instance, upgrading BRC20 to support brc20_swap requires consensus among off-chain indexers.

5. **DataFormat**: 
   - **Challenge**: Selecting an appropriate data format or structure for storage.

6. **Asset Issuance**: 
   - **Challenge**: Deciding whether to include a built-in strategy for initial asset distribution.
   - **Trade-offs**: Balancing decentralized asset issuance with user participation in the initial distribution process.

## Development Stage
BHO is currently in the design and conceptualization phase, actively addressing the outlined challenges and trade-offs.

## Comparative Analysis of Bitcoin Extension Protocols
Here is a simplified comparison of BHO with other prominent Bitcoin extension protocols:

Certainly! Here is the updated comparative analysis table of various Bitcoin extension protocols:

| Feature/Protocol   | BHO (Proposed) | Ordinals (Inscription)        | BRC-20                    | Atomicals          | SRC20                 | RGB             | Taproot Assets | Runes       |
|--------------------|----------------|-------------------------------|---------------------------|--------------------|-----------------------|-----------------|----------------| ------------|
| Data Embedding     | ?              | Witness                       | Witness(In Inscription)   | Witness            | TxOut::ScriptPubkey   | OP_RETURN       | ?              | OP_RETURN   |
| Asset Type         | ?              | NFT                           | FT                        | NFT/FT             | FT                    | ?               | FT             | FT          |
| UTXO Trace         | [#1](i1)       | Yes                           | Yes                       | Yes                | Yes                   | ?               | Yes            | No          |
| Extensibility      | ?              | ?                             | Protocol Upgrade          | ?                  | ?                     | Contract        | ?              | ?           |
| DataFormat         | [#2](i2)       | Arbitrary content & Cbor meta | JSON                      | Cbor dict          | JSON                  | ?               | ?              | ?           |
| Asset Issuance     | ?              | Issuer mint                   | User mint                 | User PoW Dmint     | ?                     | ?               | ?              | ?           |


### Explanation of Terms:
- **Data Embedding**: Method of incorporating data into Bitcoin transactions.
- **Asset Type**: Nature of the assets supported (e.g., NFTs, tokens).
- **Fungibility**: Whether assets are fungible or non-fungible.
- **UTXO Trace**: Use of UTXO for transaction tracking.
- **Extensibility**: Ability to incorporate third-party enhancements or programming features.
- **Storage**: Method of data storage and retrieval.
- **Asset Issuance**: Mechanism for creating and distributing assets.


## Reference

* [Ordinals (Inscription)](https://docs.ordinals.com/): Inscriptions inscribe sats with arbitrary content, creating bitcoin-native digital artifacts, more commonly known as NFTs. Inscriptions do not require a sidechain or separate token.
* [BRC-20](https://layer1.gitbook.io/layer1-foundation/protocols/brc-20/documentation): brc-20 is an experimental standard that demonstrates that you can create fungible tokens on layer 1 Bitcoin by leveraging ordinal theory and inscriptions.
* [Atomicals](https://docs.atomicals.xyz/): The Atomicals Protocol is a simple, yet flexible protocol for minting, transferring and updating digital objects (traditionally called non-fungible tokens) for unspent transaction output (UTXO) blockchains such as Bitcoin. 
* [SRC20](https://github.com/hydren-crypto/stampchain/blob/main/docs/src20.md): SRC-20 is a bleeding edge specification modeled after BRC-20. Prior specifications of SRC-20 in its initial state were built on top of Counterparty transactions with specific requirements for an issuance transaction.
* [RGB](https://rgb.tech/): Post-blockchain smart contracts
* [Taproot Assets](https://docs.lightning.engineering/the-lightning-network/taproot-assets/taproot-assets-protocol): Taproot Assets is primarily an on-chain protocol. Assets are issued on the bitcoin blockchain using taproot transactions.
* [Runes](https://rodarmor.com/blog/runes/): New fungible token protocol for Bitcoin created by Ordinals author.

i1: https://github.com/BitcoinHashObject/bho/issues/1
i2: https://github.com/BitcoinHashObject/bho/issues/2