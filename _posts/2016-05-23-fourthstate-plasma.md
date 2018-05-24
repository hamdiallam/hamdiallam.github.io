---
layout: post
title: FourthState is implementing Plasma
---
Post on [medium](https://blockchainatberkeley.blog/fourthstate-is-implementing-plasma-6fe99019edb2)  

## The Problem
Ethereum, like many other notable blockchains, has long been praised by the community for its ability process payments and run applications with no central controlling authority.
However, there is a plaguing issue holding all blockchains back from revolutionizing the banking industry as so many people predict.
It boils down to the limited transaction capacity of a blockchain. The Ethereum network itself cannot accommodate everyone in addition to the many decentralized applications being deployed every day.
To put this in perspective, Visa, one the largest payments processors the world uses today can handle an upwards of 42,000 transactions per second and regularly processes 150 million transactions every day globally!
In comparison, Ethereum to date, processes on average a measly 10–30 transactions per second. This cannot compete with our current payment processors.
While other blockchains such as NEO use alternative consensus mechanisms to enable a higher throughput, ~1000 tps, it still isn’t nearly fast enough to be a global payment processor.

Currently, most blockchains follow the “one size fits all” approach. Decentralized applications, contract calls, and individual transactions are all processed in an identical fashion and compete to be mined in the same block.
We all experienced the bottleneck CryptoKitties caused as the app skyrocketed in popularity; users and other dApps had to pay enormous fees to have the transactions mined and suffered long confirmation times even though their transactions were completely unrelated to the ongoing CryptoKitty craze.
Simply separating unique applications and payments from one another will massively alleviate the scalability problem. Plasma is a proposed solution to enable this at the Layer 2 level,
which means that most existing blockchains can adopt it without a hard fork. While a working solution to this has not been deployed, Blockchain at Berkeley’s FourthState team is implementing Plasma to bring blockchains to a global scale.

## Plasma
Plasma MVP(minimum viable product) brings transactions and applications off chain and leverages the Ethereum network, or any other large blockchain as the “source of truth”.
These transactions are mined on an entirely independent blockchain with a much higher throughput. In our implementation, we are utilizing the Tendermint consensus mechanism to run our sidechain.
Users can join this plasma chain by depositing funds to the smart contract deployed on Ethereum and spend those funds with other users on the sidechain.
By construction, the participants of these side plasma blockchains are guaranteed security against theft and can safely exit their funds in the presence of malicious activity.
To avoid the complexity of explaining these guarantees in this post, the way user security is ensured can be observed in the research documents in our plasma-research repo,
as well as in the original whitepaper by Vitalik and Joseph Poon, which is included in the resources section below.

The beauty of Plasma is that it is generalizable to more than just payments. The consensus mechanism used by the sidechain is agnostic to the “source of truth” smart contract.
This allows for custom protocol-level logic to create application specific blockchains that are all pegged against the same “source of truth” parent chain such as Ethereum.
One can imagine a scenario where CrypoKitties, instead of being a smart contract, is its own plasma blockchain maintained by the core developer themselves.
Users of the application can join the CryptoKitty blockchain through the “source of truth” smart contract and can have the transactions mined off-chain in this application specific blockchain.
Rather than clogging the Ethereum network with Cryptokitty transactions, users can each make one deposit transaction on the parent chain and then continue transacting on the sidechain,
leaving the Ethereum network free to process other transactions. By deploying decentralized applications in this fashion, the throughput of the Ethereum network increases exponentially.
The FourthState team plans to release a Plasma SDK which will enable dApp developers to quickly spin up these blockchains without worrying about the underlying infrastructure.

Plasma MVP was originally a spec outlined by Vitalik Buterin and Joseph Poon in a whitepaper and was briefly summarized in the ethresearch forum, which is included in the resources section below.
Since then, several different teams around the world have taken on the task of implementing a working version. Blockchain at Berkeley’s FourthState team is one with their work hosted here.

## Current Progress

At the time of this publication, the FourthState team has completed most of the rootchain smart contract work. We’re currently in the process of iterating and improving our smart contract design as well as building out the sidechain using the Cosmos-SDK which allows us to leverage the Tendermint consensus mechanism.
We’re continuing to put out research documents relevant to all Plasma implementers on our own research repo as well as the ethresearch page. Throughout this upcoming summer 2018 and onwards, there will be public weekly Zoom conference meetings regarding our implementation that the public can join.
The topics range from optimizing design choices to safety against attack vectors. These meetings will be recorded and also posted on the FourthState Youtube channel.

As a team, we are excited to announce that we have secured funding from the Ethereum foundation in support of our project. We are ahead of schedule on our timeline and aim to have simulations and a working plasma side chain by the end of August.
We always welcome individuals who would like to contribute to this awesome project. Details are continually discussed publicly in the #plasma-dev channel on the Blockchain at Berkeley slack.
Contributing guidelines are laid out in the respective repos in the organization’s GitHub.

## Resources

FourthState research repo:

https://github.com/fourthstate/plasma-research

FouthState organization repo:

https://github.com/fourthstate

Plasma whitepaper by Joseph Poon and Vitalik Buterin:

https://plasma.io/plasma.pdf

Brief overview of the plasma MVP spec by Vitalik Buterin:

https://ethresear.ch/t/minimal-viable-plasma/426

Blockchain at Berkeley’s public slack:

https://berkeleyblockchain.slack.com

Ethereum foundation May 2018 cohort for grants:

https://blog.ethereum.org/2018/05/02/announcing-may-2018-cohort-ef-grants/
