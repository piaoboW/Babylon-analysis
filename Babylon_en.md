# Babylon: an extremely appealing protocol scaling Bitcoin to secure PoS chains</b>  


## 1. Background

As of September 21st, the total value locked (TVL) in cryptocurrency was approximately $86 Billion according to DefiLlama data. Bitcoin accounts for over $10 Billion of this, reflecting a strong demand for multi-cryptocurrency staking in the market. According to data from coingecko.com, Bitcoin's current total market capitalization is approximately $1200 Billion (21 million X $62,000 USD/coin), with a circulating supply of 19,757,462 coins, roughly 9.4% of the total supply. Furthermore, data from Coinshares in March last year revealed that 25% of the circulating Bitcoin supply has been idle for over five years, 67% for over a year, and over 66% of the circulating supply remains in its current state. This large volume of idle Bitcoin not only represents a waste of assets but also fails to leverage Bitcoin's powerful security and decentralization advantages, hindering the development of the blockchain ecosystem. Lending or staking Bitcoin is a viable approach to revitalizing these assets, with applications including crypto lending and Bitcoin bridging. The primary concern in revitalizing Bitcoin assets is security, followed by flexibility and yield.

The blockchain world, beyond Bitcoin, has witnessed the rise of Ethereum as a valuable public chain. Both have maintained their leading positions due to their core values of security, decentralization, and value consensus. In the Ethereum ecosystem, EigenLayer, a renowned re-staking protocol, leverages unique design and technological innovation to enable application chains to share the security of the Ethereum ecosystem. This security is underpinned by Ethereum assets, and stakers can earn rewards through staking. For Bitcoin, security is primarily based on the massive hash power of Proof-of-Work (PoW) miners. As mining difficulty increases, the world's most secure blockchain becomes even more secure. Compared to the modular approach of re-creating a blockchain with comparable security to Bitcoin and Ethereum while offering superior cost and performance, or relying on a sufficiently secure Layer 1 as the third layer or partial functional layer for Rollups, leveraging the security of the most secure public chain, Bitcoin, to create shared security services is a viable option, exemplified by Babylon. It inherits the security of the Bitcoin chain while granting its assets more value and flexibility.

## 2. Babylon Protocol

PoS (Proof-of-Stack) chains boast high energy efficiency and rapid finality, but they face several security vulnerabilities: susceptibility to unpunishable long-term security attacks, low active elasticity, and difficulty in launching from low token valuations. Without external trusted sources, PoS chains alone cannot resolve these security issues. The Babylon Protocol, a suite of Bitcoin staking protocols, allows Bitcoin holders to stake their Bitcoin without trusting any third party, offering security guarantees for staked assets. The protocol's key lies in sharing the security features of the Bitcoin chain. However, what specific Bitcoin features can be shared by the Babylon Protocol?

2.1 Bitcoin Features

* A. UTXO (Unspent Transaction Outputs)

The UTXO model, designed by Satoshi Nakamoto for Bitcoin, operates on an incredibly simple principle. Transactions involve the movement of funds, and the entire transaction system can be represented using only inputs (Input) and outputs (Output). UTXO refers to the remaining funds when not all the incoming funds are spent; this represents unspent transaction outputs (unpaid Bitcoin). Essentially, the Bitcoin ledger is a collection of UTXOs. Each UTXO's status is recorded to manage Bitcoin ownership and circulation. Every transaction consumes old UTXOs and generates new ones. This attribute offers potential for scalability.

* B. Bitcoin Timestamping

Bitcoin timestamping relies on a timestamp server. This server works by timestamping the hash of a set of records (items) called a block and then broadcasting the hash. Each timestamp's hash is integrated with the previous one, forming a chain. Subsequent timestamps strengthen the previous one. This operation is supported by PoW (Proof-of-Work). The timestamp mechanism provides an irreversible time order for events.

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src=fig_Babylon/image.png width = "80%" alt=""/>
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">
      <p align="center"><font face="黑体" size=3.>Figure 1. Hash Value Calculation in the Bitcoin Blockchain Includes the Hash of the Previous Block

</font></p>
      </div>
</center>

* C. Multi-Signatures

In the Bitcoin blockchain, to prevent the loss of funds in an address due to the loss of a single private key, Bitcoin introduces a multi-signature mechanism. This means that a transaction requires two or more signatures for validation, enabling risk diversification. Multi-signatures allow for N individuals to hold private keys, where M individuals' consent is needed to spend funds. Bitcoin's multi-signature system allows up to 15 private keys to participate in signing, enabling any combination from 1-2 to 15-15 (1⩽M⩽N⩽15). Bitcoin utilizes Schnorr signatures for multi-signatures, which are mathematically proven to be secure. Additionally, Schnorr signatures enable signature aggregation. This means that through a technique called key aggregation, the m signatures in any "m of n" multi-signature can be aggregated into a single signature, and the m signers' public keys can also be aggregated into one. This is applicable to aggregating multiple signatures in a single input of a UTXO and supports batch verification.

* D. Bitcoin Script

Bitcoin Script, often considered the hidden force behind Bitcoin's vibrant world, is a crucial element in maintaining the security and efficiency of Bitcoin transactions. One of its most notable features is Turing incompleteness. Unlike Turing-complete languages that can execute infinite loops, Bitcoin Script's design limitation is intentional. It enhances system security, provides predictability, and effectively prevents risks associated with infinite loops. Bitcoin Script is based on various opcodes such as OP_ADD (addition) or OP_EQUAL (equality), and crucially includes opcodes like OP_CHECKSEQUENCEVERIFY and OP_CHECKTEMPLATEWERIFY that are used in the Babylon protocol.

### 2.2 Babylon Protocol Security

Bitcoin staking is a two-sided market: one side consists of PoS chains with security needs and a willingness to pay for them, while the other side comprises Bitcoin holders with capital and a desire to earn rewards. Bitcoin staking protocols need to provide strong security guarantees for both parties.

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src=fig_Babylon/image-1.png width = "90%" alt=""/>
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">
     <p align="center"><font face="黑体" size=3.>Figure 2. Bitcoin staking is a two-sided market place</font></p>
     </div>
</center>

The Babylon Bitcoin staking protocol, when integrated with existing PoS chains, exhibits three crucial security properties:

* ***Fully Penalizable PoS Security***: It ensures accountability for staking violations, requiring only a two-thirds majority of stakers to adhere to the PoS protocol for the chain to maintain good activity.

* ***Staker Security***: Each honest staker can unbind their staked Bitcoin at maturity or before maturity.

* ***Staker Liquidity***: Stakers can securely and quickly unbind their staked Bitcoin without community consensus.

These security features of the Babylon protocol rely on shared elements of the Bitcoin chain. Through innovative design, staked Bitcoin assets are remotely held on the Bitcoin chain, while leveraging the accountability and penalizability features of PoS chains to provide fundamental security guarantees. The protocol's functionalities are implemented using Bitcoin's UTXO model, timestamps, multi-signatures, and scripts.

Generally, Bitcoin stakers can be categorized into two groups: honest stakers and violators. The Bitcoin staking process within the Babylon protocol framework is illustrated below:

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src=fig_Babylon/image-2.png width = "90%" alt=""/>
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">
     <p align="center"><font face="黑体" size=3.>Figure 3. The Process of Honest Bitcoin Staking vs. the Process of Violating Bitcoin Staking
     </font></p>
</center>  

In implementing the two distinct Bitcoin staking processes mentioned above, Babylon utilizes two protocols: the first is called Bitcoin Staking, and the second is Bitcoin Time Stamping.

#### 2.2.1 Bitcoin Staking Protocol

Within the Babylon protocol, Bitcoin holders stake their Bitcoin on the Bitcoin chain without needing to trust any third party, achieving "trustless" staking. This means the staked Bitcoin is locked in a contract on the Bitcoin chain. When a staker violates the PoS chain protocol, their staked Bitcoin is penalized on the Bitcoin chain. This is a form of "remote staking."

While the Bitcoin chain lacks a smart contract layer, staking contracts can be expressed through UTXO transactions within Bitcoin Script language. The Babylon staking protocol leverages the Bitcoin chain's UTXO model and existing opcodes to break down the specific steps of a staking contract into four phases: locking funds, condition verification, state update, and reward distribution.

Analyzing the staking process from a transactional standpoint, it primarily involves three types of transactions:

* (1)Staking Transaction: BTC stakers establish a staking transaction to acquire voting rights.

* (2)Unbinding Transaction: Bitcoin stakers, prior to their staked assets maturing, can unbind their staked assets using an unbinding transaction.

* (3)Penalty Transaction: When a Bitcoin staker (or their delegated finality provider) violates the protocol, a penalty transaction is executed.

Flowchart for Bitcoin Staking in Babylon Protocol:

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src=fig_Babylon/image-3.png width = "90%" alt=""/>
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">
     <p align="center"><font face="黑体" size=3.>Figure 4. Flowchart for Bitcoin Staking in Babylon Protocol</font></p>
      </div>
</center> 

These steps, transactions, and processes require corresponding mechanisms and technologies to ensure their execution. Within the Babylon staking protocol, these include:

* A. Staking

The Babylon protocol employs a Bitcoin covenant emulator to execute staking contracts. Bitcoin covenants are a series of Bitcoin scripts capable of implementing simple smart contract functionalities like staking, redemption, and slashing. The covenant emulator is a daemon program that functions like a Virtual Machine (VM). It provides an execution environment for Bitcoin contracts and hardware, translating contract code into Bitcoin scripts for execution. Ultimately, the output is converted into UTXOs for on-chain inclusion, effectively introducing smart contracts to the Bitcoin network to enhance its programmability. The emulator is run by members of the covenant committee. The committee's role is to protect the Babylon PoS system from attacks by Bitcoin stakers and validators. This is achieved through multi-signature co-signing of transactions. The public keys used by the committee members for multi-signature are recorded in the genesis file of the Babylon blockchain.

* B. Automatic Penalty Slashing

The Babylon protocol leverages accountable assertions and finality gadgets to implement automatic slashing of Bitcoin. Accountable assertions can be implemented using Extractable One-Time Signatures (EOTS). Furthermore, to enforce penalties in consensus protocol scenarios, the Babylon protocol, without altering the underlying consensus protocol's signature scheme, introduces an additional round of EOTS signature voting following the final block of the underlying consensus protocol. This is known as a finality gadget and incorporates multi-signatures. EOTS can be implemented using Bitcoin Schnorr signatures. If a block is not only finalized by the underlying consensus protocol but also "receives" EOTS signatures from over two-thirds of the staking stake, it is considered truly finalized. Under this modified protocol, if an event occurs that undermines the integrity of the blockchain, it implies that over one-third of the stake signed two blocks at the same height using EOTS. This leads to the extraction of these stakers' private keys, which can be used to execute slashing transactions.

* C. Fast Unbinding

In native staking PoS chains, unbinding takes a long time because the blockchain requires community consensus to resist remote attacks. The Babylon protocol utilizes the Bitcoin timestamping protocol to tightly synchronize the PoS chain with the Bitcoin chain, eliminating the need for community consensus and reducing the unbinding time to one day.

Based on technologies like the Babylon staking contract, automatic penalty slashing, and fast unbinding, the core infrastructure of the Bitcoin staking protocol is the control plane between the Bitcoin chain and the PoS chain, as shown in the figure. The control plane handles various critical functions, including providing Bitcoin timestamp services, staking registration, and finality signatures. The control plane is implemented as a chain to ensure its decentralization, security, censorship resistance, and scalability. Beyond the fundamental consensus protocol tasks of block formation and validation, each validator on the PoS chain also signs finality signatures on the finality gadget. These validators collectively operate the data plane of the architecture.

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src=fig_Babylon/image-4.png width = "90%" alt=""/>
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">
      <p align="center"><font face="黑体" size=3.>Figure 5. A system structure composed of control and data planes</font></p>
      </div>
</center> 

#### 2.2.2 Bitcoin Timestamping Protocol

The Bitcoin Timestamping Protocol is a critical component of the Babylon protocol. It allows for any data, in a concise and verifiable format, to be sent to the Bitcoin chain. Its primary purpose is to timestamp data on the PoS chain, enhancing its integrity and security, particularly against long-range attacks and forking attacks. This protocol leverages Bitcoin to provide timestamping services, the Babylon blockchain to aggregate checkpoints and offer data availability, while other PoS blockchains can use this protocol to enhance their security. This protocol constructs a hybrid blockchain system, combining the security of Bitcoin with the efficiency of PoS blockchains.

To address PoS security issues, the Babylon solution based on the Bitcoin timestamping protocol is illustrated below. It primarily involves the Bitcoin mainnet, the Babylon aggregation layer, the IBC communication protocol, and the PoS consumer chain (target PoS blockchain).

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src=fig_Babylon/image-5.png width = "90%" alt=""/>
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">
      <p align="center"><font face="黑体" size=3.>Figure 6. The Babylon solution based on the Bitcoin timestamping protocol</font></p>
      </div>
</center> 


The Bitcoin mainnet, acting as the Bitcoin timestamp server, is the core source of trust. However, the Babylon chain is the key to making the entire solution efficient and feasible. Having the PoS chain directly interact with the Bitcoin chain poses several problems:

* (1)Each PoS block containing a transaction request must be checked.

* (2)A sufficient number of signatures must be released at each checkpoint to prevent validators from sending arbitrary hashes and pretending to be checking PoS blocks on Bitcoin.

* (3)Bitcoin's limited block space presents scalability issues.

The Babylon Bitcoin timestamping process operates as follows:

* (1)Data Submission: Important data generated by nodes on the PoS blockchain, such as transaction or block information, is converted into hash values.

* (2)Submission to Bitcoin Network: The Babylon chain gathers these hashes, aggregates them into a package, and uses IBC (Inter-Blockchain Communication) to submit the collection in a specific transaction to the Bitcoin chain.

* (3)Timestamp Generation: Once these hashes are recorded on the Bitcoin chain, the PoS blockchain obtains a timestamp from the Bitcoin chain.

* (4)Timestamp Usage: The PoS blockchain can utilize the Bitcoin timestamp to verify the security and timeliness of its data.

The core principle of security offered by Bitcoin timestamps within the Babylon protocol is illustrated in the following diagram:

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src=fig_Babylon/image-6.png width = "90%" alt=""/>
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">
     <p align="center"><font face="黑体" size=3.>Figure 7. The core principle of security offered by Bitcoin timestamps</font></p>
</center> 

Attacking Branch Disadvantage: Any attacking branch that receives a later Bitcoin timestamp on the BTC main chain will not be selected by any consuming PoS chains, according to the branch selection rules.

Economic Infeasibility of Attacking Branch Recognition: If an attacking branch wishes to be recognized, it needs to create a very long branch on the BTC chain to give the PoS branch an earlier timestamp. However, this is economically unacceptable.

This mechanism ensures that any attempts to manipulate the PoS blockchain by forging timestamps will be unsuccessful.

#### 2.2.3 Additional Security Benefits

Beyond addressing long-range attacks, irreversible BTC timestamps on PoS blocks offer further security benefits:

* ***Eliminating Weak Subjectivity***: Bitcoin timestamps are objective. This removes the PoS chain's reliance on social consensus and weak subjectivity.

* ***Shorter Unbinding Time***: By replacing social consensus, BTC timestamps can shorten the staking unbinding time for PoS chains from weeks to a day.

* ***New Chain Bootstrapping***: New PoS chains with lower valuations are more susceptible to forking attacks. BTC timestamps can help protect the chain's growth.

* ***State Synchronization and Snapshot Validation***: The objective facts provided by BTC for PoS chains allow PoS chain users to validate chain state or snapshots downloaded from the P2P network.

* ***Protecting Important Transactions***: BTC timestamps can be used to further confirm important PoS transactions, but at the cost of longer confirmation delays.

* ***Censorship Resistance***: BTC timestamps can also be used to resist transaction censorship in PoS chains by publishing censored transactions to BTC.

### 2.3 Conclusion

In summary, the Babylon protocol leverages various features of the BTC chain through innovative design, enabling PoS consumer chains to share the security of the BTC chain. While the security and performance of the Babylon protocol need practical validation, the security of the PoS consumer chain ultimately depends on its inherent security, not Bitcoin network or the Babylon protocol. This presents a challenge for the Babylon protocol's ecosystem.

## 3. Considerations

The Babylon protocol, as a modular plugin, acts as an intermediary layer connecting the Bitcoin chain and PoS consumer chains. Bitcoin holders earn rewards through remote staking, directly proportional to the amount staked.This raises several considerations:

* ***Centralization Risk***: The reliance on a single protocol could lead to centralization risk.

* ***Staking and Allocation Issues***: Different stakers have varying motivations and resources. This could lead to imbalances in supply and demand, requiring mechanisms to adjust staking asset allocation. PoS chains in their early stages, particularly, might struggle to compete for staking assets.

* ***Staking Asset Rewards***: If Bitcoin's staking rate is too low, it could significantly impact the project's development. Over time, staking rewards will naturally decline. When the return rate drops below a certain threshold, Bitcoin holders may lose interest, leading to the project's stagnation or decline.

* ***Demand Uncertainty***: The demand for security on the consumer side is highly uncertain. If demand does not align with supply, the entire economic cycle cannot be realized.

On the evening of August 22nd, the Babylon Bitcoin staking project launched its first phase of the mainnet, attracting significant attention from crypto users. Due to the surge in transaction volume, frequent operations, and large-scale congestion on the Bitcoin network, Bitcoin network gas fees soared from $0.5 to $132, resulting in losses for many retail investors due to high gas fees. Furthermore, the total amount staked in this phase was only 1000 BTC. When the total amount staked increases by several orders of magnitude, can the Bitcoin network support it while maintaining low gas fees? Additionally, the staking in this phase only rewards users with Babylon points, and the sustainability of its rewards remains to be seen.

## Reference

[1] https://docs.babylonchain.io/docs/

[2] Bitcoin-Enhanced Proof-of-Stake Security: Possibilities and Impossibilities

[3] Bitcoin Staking: Unlocking 21M Bitcoins to Secure the Proof-of-Stake Economy

[4] Bitcoin: A Peer-to-Peer Electronic Cash System

[5] https://www.techflowpost.com/article/detail_19080.html

[6] https://www.techflowpost.com/article/detail_19080.html

[7] https://www.youtube.com/watch?v=LoVpMH8-CiQ&ab_channel=ChrisHacks

[8] https://www.techflowpost.com/article/detail_19080.html



