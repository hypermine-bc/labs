---
title: "Introduction to Inter-Blockchain Communication (IBC) Protocol"
date: 2022-01-04T12:30:05+05:30
draft: false
categories: ["crosschain", "blockchain"]
tags: ["blockchain", "did", "cosmos", "HID", "hypersign"]
banner: "/images/ibc-blog/ibc-cosmos.svg"
authors:
  - arnab
---

At Hypersign, we are working towards building our network and researching about some of the popular frameworks to choose from. Cosmos and Polygon are top on our list. A quick bite about the Hypersign Network before we move on: 

> **Hypersign Identity Network** - A simple, secure and affordable blockchain network for managing digital identity and access rights without compromising on security and privacy. The network also incorporates privacy subchains and interoperability between them. 

There are many factors that needs to be considered before going ahead with a network. One such factor is **interoperability**. Since the core concept that we are going to use in this network is [Self Sovereign Identity (SSI)](https://en.wikipedia.org/wiki/Self-sovereign_identity),  where a user can issue an identifier called **decentralised identifier** (DID) to himself, interoperability of DID between different blockchains becomes important factor for adoption of that network. What we essentially want is, a DID issued on one subchain, should be able to get resolved on the other. I will write a seperate blog post about Hypersign Identity Network some time later, but in this blog post let's explore **IBC protocol** to understand how a token from one network can be transferd to another network (also called zones) in Cosmos ecosystem. 

## What is IBC?

IBC, or Inter-Blockchain Communication is a protocol standard by means of which blockchains can interoperate among each other, such as through transfer native assets or account delegation. The data transfer happens permissionlessly. It is the protocol used by chains in the Cosmos Ecosystem.

The protocol, however, requires that the blockchain should have their consensus based on fast-finality rather than probabilistic finality. Consensus mechanisms such as Proof-of-Stake and Proof-of-Authority fall under fast-finality, while Proof-of-Work consensus falls under probabilistic finality. The Cosmos team has been working towards bridging Proof-of-Work based chains like Ethereum with Cosmos using Peg Zones.

So where does IBC fits in a blockchain? IBC lies between the application layer which constitutes of modular executable code (for instance, smart contracts) and the core consensus and networking layer. Implementation of IBC doesn’t require the blockchain to go through any fundamental changes. The requirements it possess is that the blockchain should provide Key-Value pair style storage mechanism from where IBC can perform its operation. For instance, a key-value pair can be assigned to store the consensus state.

## The Architecture

The acrhitecture of IBC consists of 2 years: TAO (Transport, Authentication and Ordering) and APP (Application Oriented) layer. TAO comprises of the core infrastructure of protocol, and the APP layer comprises of a set of applications (for example, Token Transfer) which can be framed on top of the core protocol. We will now look at some of the concepts of Core protocol.

#### Client

Clients (or light clients) are the authenticatiom component which represents the properties of the consensus algorithm which are necessary efficient state verification of its corresponding blockchain. An example could be Bitcoin SPV, which is a light client of bitcoin. Consider two blockchains - Blockchain A and Blokchain B - that want to interoperate. Blockchain A will have its light client deployed on Blockchain B, and Blockchain B will have it light client deployer on Blockchain A.

In an event of token transfer from Blockchain A to Blockchain B, the counterparty blockchain requires a consensus transcript proof from source blockchain indicating that the tokens have been deducted from the user on Blockchain A. This proof is recieved on Blockchain B, where the light client executes the logic to prove the inclusion of transaction on source ledger, following which the same transactions is replicated on Blockchain B.

Some examples of light client includes: Tendermint light client, solomachine light client. Many networks that are not build on top of Tendermint Core, are working on building their light clients.

#### Connection

Now that we know about Clients, its time to connect them. This is done by Connection. There are two stateful objects, called Connection End, deployed on both chains which establishes the link with the Client. This linkage is done through a three-way handshake protocol.

#### Channel

Channel act as a pathway for transfer of packets between modules on separate blockchains. It ensures that the packets are delivered exactly once, in ordered manner (if configured) and delivered to the right module on the receiving chain. A connection can constitute of multiple channels. The channels are linked through 3-way handshake protocol, similar to how Connections are linked as we have seen. Channels can be configured to be Ordered where each packet is sequenced, or Unordered.

#### Relayer

Relayers are the off-chain nodes which physically relay the packet between the IBC connnected ledgers. Ledgers don’t send the data directly, but merely commit an intent to transfer it. Relayers continuously scan the ledgers on particular path (Key-Value store), where the ledgers commits the intent on transferring the packet. A channel can consist of multiple relayers, and at least one relayer should be live for a reliable IBC transfer.

#### IBC Demo - Token Transfer

In this demo, we will be transferring ATOM tokens from Cosmos Network to Osmosis Network, and again redeem the ATOM voucher minted on Osmosis Network back to Cosmos Network.

1. First we will head to [Mintscan](https://www.mintscan.io/) which is one of the Block Explorers for the Cosmos Ecosystem.
2. Mintscan is a unified platform where explorers of all blockchains present in Cosmos Ecosystem can be accessed. Right now, we are on the *Cosmos* Block Explorer Page. Since our source chain is Cosmos, we will leave it to that.

Now click on the **IBC Relayers** tab

| ![Figure (i)](/images/ibc-blog/img_1.png)
|:--:|
| *Figure (i)* |

3. We can see a list of relayers of blockchains which connect with Cosmos Hub. Since our destination chain is Osmosis, scroll down and click on **Osmosis**

| ![Figure (ii)](/images/ibc-blog/img_2.png)
|:--:|
| *Figure (ii)* |

Here, we can a list of channels between **Cosmos** and **Osmosis**.  Reliability of a channel depends upon its transaction activity. The first channel clearly shows the activeness, and hence we will be going ahead with this channel.
Note the channel identifies:

- **Cosmos:** channel-141
- **Osmosis:** channel-0
4. Open the **Kepler Wallet** Extension. The default network is Cosmos. We currently have 0.067 ATOM coins. **Send** button will transfer ATOM tokens with other Cosmos wallet on the blockchain. In order to send tokens to other chains, click on the **IBC Transfer**. 

![Figure](/images/ibc-blog/img_comb_1.png) 


5. Click on the **Destination Chain** dropdown. Initially, we won’t have any channel path saved. To create one, click **New IBC Transfer Channel**. In Figure (v), select the **Destination Chain** as **Osmosis** and **Channel ID** as **channel-141**. The reason for entering **channel-141** is because it is the source channel ID on the Cosmos side (Refer Step 3). Click **Save** and select the new channel is created. Enter the recipient’s address and Memo, if needed, and click **Next.**
6. Enter the amount of tokens to be sent and the Gas Fees, and hit **Submit**. On the next screen, review the details of transaction, and click **Approve**. And that’s it! Vouchers are now on the Osmosis side as seen in *Figure (viii)*

![Figure](/images/ibc-blog/img_comb_2.png) 

#### Behind the scenes

- Acting as the source ledger, the ATOM tokens were escrowed on the Cosmos End.
- The information about sending ATOM tokens, were transferred through the channel (**channel-141** <-> **channel-0**) with the help of relayers.
- Upon receiving the packet and acting as the sink ledger, equivalent ATOM vouchers (**ATOM (COSMOS/CHANNEL-0)**) are minted on the Osmosis side.
- The acknowledgement message of the packet being received on the Osmosis End, is relayed to Cosmos.

### Conclusion

The Cosmos ecosystem is expansive. It envisions not only to connect chains with instant finality such as Proof-of-Stake and Proof-of-Authority, but also have the infrastructure laid out to connect Proof-of-Work based chains as well. This expands the spectrum of things that we can do with the blockchain, which makes Cosmos an interesting project to look forward to.
