# [Consensus](https://en.wikipedia.org/wiki/Consensus_(computer_science)#cite_note-PSL82-9) 

Moonwon Lee @ berkeley.edu



## 1. Purpose of This Note
1. Background : I got an internship at a blockchain company during my winter vacation, then I started studying blockchain. I had zero knowledge of blockchain before. I did not have enough time so I just read through every document on google in a random order. It was like jumping around, filling gaps of my knowledge in blockchain. As I read more and more, I got more questions about this special chain. It felt like an endless loop (especially PoS, Paxos, Correctness of consensus, and Implementation of blockchain and smart contract). Then, I realized that Blockchain was an evolving field, therefore it was far from being perfect unlike different fields I studied in college (I’m math major). The origin of blockchain was very clear : Everyone can see everything and they are shared by everyone. However, as people are trying to do more things with this promising chain, the pure idea has been transformed into ugly and less clear shape. Now, the blockchain is not really open to everyone and the blockchain is not as simple as its name. [It’s a lot more than a block and a chain.](https://hyperledger-fabric.readthedocs.io/en/release-1.4/network/network.html) Finally I have realized that why blockchain is so confusing and difficult to understand: the ideal of blockchain is keep colliding with its realization. Here in this codument, I copy-pasted sentences that helped me to understand blockchain.
2. About this Doc.
    1. This is a very personal note consisting of sentences that I collected for myself. That is why everything in this doc is indexed (my memo skill). 
    2. Citation might not be perfect. I did my best though.
    3. Choice of words might be poor and offensive. I said personal.
    4. I added as many links and citations as possible for further reading.
3. Missing Contents
    1. Smart Contract : Not a main topic here.
        1. I spent a lot of time trying to understand Smart Contract since I could not imagine how blockchain can do it. It was hard to understand how Smart Contract is realized on Blockchain conceptually and how it can be implemented in reality. I think it is because Smart Contract is not a super natural form of Blockchain(even though everyone says it is natural). It is like a layer on top of Blockchain. It is somewhat in the middle of Blockchain and Database. The best way to understand Smart Contract is to see examples of its implementation. I recommend reading [Hyperledger Fabric’s Blockchain network](https://hyperledger-fabric.readthedocs.io/en/release-1.4/network/network.html).
    2. Cryptography : Not a main topic here.
      1.Some knowledge of Cryptography is required to fully understand Blockchain.
        Recommend following readings
        1. The first chapter of [Handbook of Applied Cryptography](http://cacr.uwaterloo.ca/hac/).  It took me 8 hours.
            1. [A Brief Summary of Cryptography for Blockchain](https://docs.google.com/document/d/1IUGXtIyu55TYunM0_g3b99HzDN1ehv_lFeM3hJTBjvo/edit#heading=h.ywu36ukcepfm) by Moonwon Lee @ berkeley.edu
        2. UC Berkeley, CS70 Summer 2019, [Public Key Cryptography Note 7](https://www.su19.eecs70.org/static/notes/n7.pdf) 
        3. UC Berkeley, CS70 Spring 2017, [Bijactions and RSA Note 7](http://sp17.eecs70.org/static/notes/n7.pdf).
        4. And some more on [Elliptic Curve Cryptography](https://en.wikipedia.org/wiki/Elliptic-curve_cryptography)
    3. Block : Not a main topic here. 
        1. Some knowledge of a block is required to fully understand Blockchain.
            1. Secure Hash Algorithms
            2. Pseudorandom
            3. Merkle Tree
## 2. Similar to what I want to accomplish in this note : 
[A brief history of Consensus, 2PC and Transaction Commit.](http://betathoughts.blogspot.com/2007/06/brief-history-of-consensus-2pc-and.html)
## 3. Main Players in Chronological Order
1. [Leslie Lamport](https://en.wikipedia.org/wiki/Leslie_Lamport)
    1. [Turing Award](https://en.wikipedia.org/wiki/Turing_Award) Recipient in Distributed Computing, 2013
        1. Consensus in [Distributed Network](https://en.wikipedia.org/wiki/Distributed_networking)
        2. the Mathematical Ground for Consensus and Distributed Network. 
        3. [The Byzantine Generals Problem](http://lamport.azurewebsites.net/pubs/byz.pdf), 1982. [Byzantine Fault Tolerance](https://blog.goodaudience.com/the-byzantine-generals-problem-d979c5d8c467) 
    2. MIT -> [SRI Int](https://en.wikipedia.org/wiki/SRI_International). -> Microsoft
    3. [The Writings of Leslie Lamport](http://lamport.azurewebsites.net/pubs/pubs.html)
2. Miguel Castro, MIT
    1. [PBFT](http://pmg.csail.mit.edu/papers/osdi99.pdf), 1999
3. [Satoshi Nakamoto](https://en.wikipedia.org/wiki/Satoshi_Nakamoto), anonymous
    1. Whitepaper : PoW + Blockchain = Bitcoin
4. [Bitcoin](http://bitcoin.org), 2009
5. [Ethereum](https://en.wikipedia.org/wiki/Ethereum), 2015
6. [Hyperledger](https://en.wikipedia.org/wiki/Hyperledger) by the Linux Foundation + IBM, 2015
7. [Nexledger by Samsung](http://www.theinvestor.co.kr/view.php?ud=20170406000977), 2016
8. [Libra by Facebook](https://libra.org/en-US/white-paper/), June, 2019 \

## 4. Bigbang of Blockchain: [Proof of Work](https://blog.goodaudience.com/how-a-miner-adds-transactions-to-the-blockchain-in-seven-steps-856053271476?)
1. Blockchain: 
    1. Core to the blockchain is the model of the ledger, an unalterable, append-only log of the transactions that take place across various entities. To maintain the integrity of the ledger, the various entities need a way to “agree” or to reach consensus on which set of incremental transactions (or blocks) are to be appended to the ledger [1].
    2. Widely known as the core technology underpinning the digital currency, blockchain refers to a ledger that maintains a continuously expanding list of data records or transactions from different parties [2].
2. Bitcoin
3. [Ethereum 1.0](https://docs.ethhub.io/ethereum-roadmap/ethereum-1.x/)
4. Weakness : 
    1. [51 percent attack](https://blog.goodaudience.com/what-is-a-51-attack-or-double-spend-attack-aa108db63474?)
          1. Solution : hope 51 percent guys would not play with their own money. If they mess up their currency, they would lose money right? 
          2. Doubt : But this will do?
    2. [Waste of Energy](https://www.theguardian.com/commentisfree/2019/jan/17/bitcoin-big-oil-environment-energy) = mining
5. My Thoughts and Questions
    1. Q: What if I mess up with the transactions and put them in a block and do mining on it and I am the fastest one for that round?
        1. First, I don’t think the block would get accepted because the others will validate my block’s txs and say mine is corrupted therefore reject it, and I believe some kind of a different consensus is needed here for this block validation. Need more research.
        2. And even though you can do this, there is no point of doing this, because you cannot make money. To add txs of my taste, I need other’s private keys which i don’t have(cryptography here~). So all I can do with messing around txs is with my money. Therefore, only malicious act I can try in PoW is[ Double Spending](https://blog.goodaudience.com/what-is-a-51-attack-or-double-spend-attack-aa108db63474?) which makes it the only possible problem in PoW.
        3. Q : So [Double Spending](https://blog.goodaudience.com/what-is-a-51-attack-or-double-spend-attack-aa108db63474?) is a problem? 
            1. A: NO! it never happens, because it requires attackers to have 51 percent of the hashing powers. 
            2. A: Furthermore, It is the chain with the highest cumulative proof of work that wins, miners have an interest in choosing the branch with the highest probability of success. If the miner chooses both chains at the same time, he will have to split his hash power for the two, and his gain expectation will therefore be lower than if he solely mines the chain that is most likely to succeed
        4. Q : But What if 51 percent actually taken somehow?
            1. A: Fucked up then. PoW proven not to be working because top 2 is taking up more than 50 percent of the cryptocurrencies based on PoW. [BitCoin](https://www.blockchain.com/pools) and [Ethereum](https://www.etherchain.org/charts/topMiners). 51 percent attack!!!!
    2. Q : What if first miner just wrote down wrong things(transactions) in its block and just did the mining and found the proper bounce?
        1. A : When a miner finds a solution, it will be broadcasted (along with their block) to the other miners and they will only verify it if all transactions inside the block are valid according to the existing record of transactions on the blockchain. Note that even a corrupted miner can never create a transaction for someone else because they would need the digital signature of that person in order to do that (their private key). Sending Bitcoin from someone else’s account is therefore simply impossible without access to the corresponding private key [3].
    3. PoW is kind of perfect….compared to other strategies.
## 5. [Proof of Stake](https://github.com/ethereum/wiki/wiki/Proof-of-Stake-FAQ)
1. Good thing : 
    1. No more waste of energy. Supposed to be better than PoW for sure!...
    2. Sharding(horizontally, not vertically) : core idea in DB, Distributed Computing, Asynchronous shit. PoW cannot do this becauses of its nature. But PoS can do it. wait, BFT can do it…
    3. Sharding -> high scalability!!
2. Weakness : [Nothing at Stake problem](https://medium.com/coinmonks/understanding-proof-of-stake-the-nothing-at-stake-theory-1f0d71bc027)
    1. Solution : punish bad guys, 
    2. Doubt : but would work?
3. My Doubts
    1. Is this PoS really a thing tho?
    2. Ethereum will move to PoS and its protocol is total mess to understand. so complicated and there are many layers. 
    3. I understand what Pos is but [does it really make any sense?](https://ethereum.stackexchange.com/questions/66572/how-does-the-network-validate-a-block-in-pos)
    4. Is there any real implementation of PoS?
        1. Ethereum 2.0 is working on it
            1. [Ethereum 2.0, Proof of Stake FAQ](https://github.com/ethereum/wiki/wiki/Proof-of-Stake-FAQ#what-is-proof-of-stake) 
            2. [A Proof of Stake Design Philosophy - Vitalik Buterin](https://medium.com/@VitalikButerin/a-proof-of-stake-design-philosophy-506585978d51)
            3. [Ethereum, Proof of Stake Design Philosophy](https://docs.ethhub.io/ethereum-roadmap/ethereum-2.0/proof-of-stake/)
4. Chain-based PoS: 
    1. PoW -> PoS(Chain) Nakamoto consensus can be generalized to refer to “chain-based” consensus at large, in which the protocol states that you must choose among several possible chains. Thus, when proof-of-stake initially became a popular alternative to proof-of-work, because it doesn’t require wastage of the vast computing power that PoW does, the first proof-of-stake consensus algorithms were chain-based. In Nakamoto-based proof-of-stake, the consensus algorithm pseudo-randomly selects a stakeholder (in proportion to their stake) and assigns them the right to create a single block. It is, in a sense, “simulated PoW” [4].
    2. Safety < Liveness : network delays and deviant actors will lead to inevitable forks. Thus, Nakamoto-based proof-of-stake favors liveness (availability) over safety (consistency) [4].
    3. Simulated PoW : The consensus algorithm pseudo-randomly selects a stakeholder (in proportion to their stake) and assigns them the right to create a single block. It is, in a sense, “simulated PoW” [4].
    4. No Chain! : What many people began to realize was that Nakamoto consensus was necessary for proof-of-work, but not proof-of-stake. Since Nakamoto PoS, in its naive form, suffers from [the “nothing at stake” problem and long-range attacks](https://blog.ethereum.org/2014/11/25/proof-stake-learned-love-weak-subjectivity/), people sought a new way to achieve PoS without relying on chain selection. In comes BFT-based proof-of-stake, or, technically, [state-machine-replication](https://en.wikipedia.org/wiki/State_machine_replication)-based proof-of-stake — which was an old innovation [4].
5. (May skip this part for now:) BFT-based PoS: 
    1. More BFT in the following discussion below.
    2. PoS + BFT = PoS not relying on a chain selection.
    3. Safety > Liveness 
    4. Examples:
        1. ETH 2.0 ([Casper](https://blockgeeks.com/guides/ethereum-casper/))
        2. Tendermint
        3. peercoin
## 6. Two Assumptions for Distributed Computing, Consensus
1. Condition 1 : Synchronous
    1. Definition :
        1. In asynchronous systems, there is no upper bound on the amount of time components (nodes, generals) may take to receive, process and respond to messages
2. Condition 2 : [Byzantine Fault](https://en.wikipedia.org/wiki/Byzantine_fault).
    1. [The Byzantine Generals Problem](http://lamport.azurewebsites.net/pubs/byz.pdf) by LESLIE LAMPORT, ROBERT SHOSTAK, and MARSHALL PEASE SRI International 
        1. It has been proven in the [original Byzantine Generals Problem paper](http://www-inst.eecs.berkeley.edu/~cs162/fa12/hand-outs/Original_Byzantine.pdf) by Lamport, Shostak, and Pease, that no solution with fewer than 3m + 1 generals can cope with m traitors; i.e., consensus is impossible to achieve if ⅓ or more of the generals are traitors [4].
        2. Byzantine fault tolerant with _<⅓n_ faulty nodes where n is the number of all nodes.
        3. Robert Shostak(founder) showed that a minimum of _3n+1_ are needed, and devised a two-round _3n+1_ messaging protocol that would work _for n=1_. Shostak formalized the problem mathematically and proved that for n faulty computers, no fewer than _3n+1 _computers in total were needed for any algorithm that could guarantee consensus, or what he termed interactive consistency [5]
            1. Robert formalized BF problem as Interactive Consistency Problem
        4. His colleague Marshall Pease generalized the algorithm for any n > 0, proving that _3n+1_ is both necessary and sufficient. [5]
        5. These results, together with a later proof by [Leslie Lamport](https://en.wikipedia.org/wiki/Leslie_Lamport) of the sufficiency of _3n_ using digital signatures, were published in the seminal paper Reaching Agreement in the Presence of Faults(1980).(Dijkstra Prize 2005) [5]
        6. 3n argument is for Byzantine not for asynchronicity
        7. But Why _3f + 1_, where _f _is the number of faulty nodes 
            1. Proof: The resiliency of our algorithm is optimal: _3f + 1_ is the minimum number of replicas that allow an asynchronous system to provide the safety and liveness properties when up to f replicas are faulty (see [2] for a proof). This many replicas are needed because it must be possible to proceed after communicating with _n - f_ replicas, since _f_ replicas might be faulty and not responding. However, it is possible that the f replicas that did not respond are not faulty and, therefore, f of those that responded might be faulty. Even so, there must still be enough responses that those from non-faulty replicas outnumber those from faulty ones, i.e.,_ n - 2f > f _Therefore _n > 3f,_ that is, _n >= 3f + 1_ [6]
        8. Then Lamport made up the allegory of Albanian army
        9. The name was changed, eventually settling on "[Byzantine](https://en.wikipedia.org/wiki/Byzantine_Empire)", at the suggestion of Jack Goldberg to future-proof any potential offense giving in [The Byzantine Generals Problem](http://lamport.azurewebsites.net/pubs/byz.pdf) [5]
        10. This formulation of the problem, together with some additional results, were presented by the same authors in their 1982 paper. [5]
        11. BFT in Korean : [Consensus over Byzantine Fault (1) - The Problem](https://suckzoo.github.io/tech/2018/02/06/bft-1.html)
## 7. Mathematical Grounds for Distributed Computing, Consensus
1. New Era about to begin with the development of Mathematics
2. Blockchain is one kind of Distributed Computing
3. [Correctness of Distributed Computing](https://medium.com/@ancapalex/a-cursory-introduction-to-byzantine-fault-tolerance-and-alternative-consensus-1155a5594f18)
    1. [Proving the Correctness of Multiprocess Programs](http://lamport.azurewebsites.net/pubs/proving.pdf) by Leslie Lamport (1977), the correctness of distributed (i.e. concurrent, i.e. multiprocess) systems can be described in terms of liveness and safety. 
    2. Safety : 
       1. Bad will never happen
       2. Safety (consistency) is guaranteed - as is the case with any state machine replication, where the nodes must reach agreement to come to consensus. 
    3. Liveness :
        1. Good will eventually happen such as consensus guarantee that each component will eventually decide on a value. A Byzantine agreement protocol would ideally also guarantee liveness, meaning that all non-faulty nodes eventually terminate and output a decision [6]
4. [The FLP impossibility](https://www.the-paper-trail.org/post/2008-08-13-a-brief-tour-of-flp-impossibility/) :
    1. Original paper : [Impossibility of Distributed Consensus with One Faulty Process](https://groups.csail.mit.edu/tds/papers/Lynch/jacm85.pdf) by [Michael J. Fischer](https://en.wikipedia.org/wiki/Michael_J._Fischer), [Nancy Lynch](https://en.wikipedia.org/wiki/Nancy_Lynch), and [Mike Paterson](https://en.wikipedia.org/wiki/Mike_Paterson)
    2. [Dijkstra Prize](https://en.wikipedia.org/wiki/Dijkstra_Prize) for this significant work. 
    3. States that both termination and agreement (liveness and safety) cannot be satisfied in a time bound manner in an asynchronous distributed system, if it is to be resilient to at least one fault (they prove their result for general fault tolerance, which is weaker than Byzantine fault tolerance, since it only requires one fail-stop node — so BFT is included inside FLP impossibility claims) [4]. 
    4. FLP <p [BFT](https://blog.goodaudience.com/the-byzantine-generals-problem-d979c5d8c467) : Byzantine is harder : If FLP is impossible, then Byzantine is impossible too by reduction.  [A Cursory Introduction to Byzantine Fault Tolerance and Alternative Consensus](https://medium.com/@ancapalex/a-cursory-introduction-to-byzantine-fault-tolerance-and-alternative-consensus-1155a5594f18)
    5. So in the asynchronous distributed system, we cannot get both safety and liveness.
    6. Unfortunately, achieving all three of safety, guaranteed termination, and fault tolerance [turns out to be impossible](https://groups.csail.mit.edu/tds/papers/Lynch/jacm85.pdf) without some additional assumptions [7].
    7. In the synchronous distributed system, we can get both by using clever ideas
    8. However, distributed system is asynchronous by birth.
    9. [The Saddest Moment](https://scholar.harvard.edu/files/mickens/files/thesaddestmoment.pdf) = Making distributed systems reliable is inherently impossible, said James mickens at Harvard 
   10. Blockchain is one kind of Distributed System. Therefore, Blockchain can never get perfect.
5. [CAP Theorem](https://en.wikipedia.org/wiki/CAP_theorem)
    1. Def : Consistency =  is a guarantee that reading from each node will return the correct (most recent) write. (guarantee that nothing bad will ever happen) [4].
    2. Def : Availability =  is a guarantee that reading from any node will return some response. (guarantee that something good will eventually happen) [4].
    3. Def : Partition tolerance = is a guarantee that the system will still operate in the face of a network partition, across which some messages between nodes cannot be delivered (fault tolerance) [4].
6. [FLP and CAP aren't the same thing](https://www.the-paper-trail.org/post/2012-03-25-flp-and-cap-arent-the-same-thing/)
7. Remark : FLP < CAP < BFT = By CAP Theorem, fault tolerant (partitioned network) consensus (availability and consistency) is unachievable in asynchronous systems. By FLP impossibility, fault tolerant (single fault) consensus (termination and agreement) is unachievable in asynchronous systems.FLP-admissible systems need only one faulty node, and messages can be delayed but not dropped (there is no network partition). CAP Theorem, thus, appears to be a particular instance of FLP impossibility [4].
## 8. New Era About to Begin...Because 
1. Proof of Work Sucks : 
    1. Environment Concerns : [Is Bitcoin a Waste of Electricity, or Something Worse?](https://www.nytimes.com/2018/02/28/business/economy/bitcoin-electricity-productivity.html)
    2. Banking Systems: 
        1. The idea of implementing a byzantine fault tolerance (BFT) consensus came from the challenges we faced while building blockchain solutions for banks. We chose ethereum as the baseline protocol mostly because of its smart contract capability. However, the built-in consensus, proof of work or ethash, is not the ideal choice when settlement finality and minimum latency is required [8].
        2. Tend to form a private chain or consortium chain to run their applications. [PBFT](http://pmg.csail.mit.edu/papers/osdi99.pdf) is ideal for these settings. These environments require a higher degree of manageability and higher throughput. In terms of scalability, validator scalability is not required. Many of the decentralization benefits of PoW in public chains become drawbacks in a private/consortium chain. On the other hand, designated validators in a PBFT environment maps well to private/consortium chains.[Istanbul Byzantine Fault Tolerance · Issue #650 · ethereum/EIPs](https://github.com/ethereum/EIPs/issues/650) [8].
## 9. Brave New World = Permissioned (Private) VS Permissionless (Public)
1. Permissionless (Public) blockchain
    1. Proof of Work consensus
    2. Proof of Stake : is there a blockchain only using proof of stake?
    3. Proof + BFT based consensus
2. Permissioned (Private) blockchain
    1. BFT-based consensus
3. Road to BFT
  1. [Paxos](https://lamport.azurewebsites.net/pubs/lamport-paxos.pdf)
     1. [The Part-Time Parliament](https://lamport.azurewebsites.net/pubs/lamport-paxos.pdf) by Leslie Lamport
        1. Dale Skeen : seems to have been the first to have recognized the need for a three-phase protocol to avoid blocking in the presence of an arbitrary single failure.  However, to my knowledge, Paxos contains the first three-phase commit algorithm that is a real algorithm, with a clearly stated correctness condition and a proof of correctness.
        2. Not BFT 
            1. But there is BFT-Paxos by Leslie Lamport
        3. At the heart of the algorithm is a three-phase consensus protocol.
        4. [Byzantine Paxos](http://lamport.azurewebsites.net/pubs/web-byzpaxos.pdf)
            1. PBFT by Castro : intuitively seems like a modification of Paxos to handle Byzantine failures, using _3f+1_ processes instead of _2f+1_ to handle f failures.  In 2003 I realized that a nice way to think about the algorithm is that_ 2f+1_ non-faulty processes are trying to implement ordinary Paxos in the presence of n malicious processes--each good process not knowing which of the other processes are malicious.  Although I mentioned the idea in lectures, I didn't work out the details [12]. 
        5. [Leaderless Byzantine Paxos](http://lamport.azurewebsites.net/pubs/disc-leaderless-web.pdf
            1. Dr. Lamport says : I have found the Castro-Liskov algorithm and other "Byzantine Paxos" algorithms unsatisfactory because they use a leader and, for progress, they require detecting and removing a malicious leader. My idea was to eliminate the leader by using a Synchronous Byzantine agreement algorithm to implement a virtual leader. The note is too short to discuss the practical details, but they seem to be straightforward [13].
  6. [Raft](https://raft.github.io/)
        1. [In Search of an Understandable Consensus Algorithm](https://raft.github.io/raft.pdf) by Diego Ongaro and John Ousterhout at Stanford University in 2013.
        2. Not BFT, only [Crash Fault Tolerance](https://stackoverflow.com/questions/56336229/byzantine-fault-tolerance-bft-and-crash-fault-tolerance-cft)
        3. 2f + 1 needed
        4. Its primary goal is understandability, since most deterministic consensus algorithms previously developed were convoluted and difficult to grasp [11]. 
        5. Raft provides crash fault tolerance, allowing a network to continue to make progress as long as at least half of the nodes are available [11].
        6. [Raft Implementation](https://www.hyperledger.org/blog/2019/01/11/floating-the-sawtooth-raft-implementing-a-consensus-algorithm-in-rust) by Hyperledger. Since not Byzantine-fault-tolerant, not suitable for consortium-style networks with adversarial trust characteristics. [11]
        7. It's equivalent to Paxos in fault-tolerance and performance. The difference is that it's decomposed into relatively independent subproblems, and it cleanly addresses all major pieces needed for practical systems.
        8. [Properties](https://www.hyperledger.org/blog/2019/01/11/floating-the-sawtooth-raft-implementing-a-consensus-algorithm-in-rust) [11]
            1. Strong leadership: Networks elect a leader that is responsible for making progress
            2. Non-forking: Unlike lottery-based algorithms, Raft does not produce forks
            3. Closed membership: Raft does not support open-enrollment, but nodes can be added and removed by an administrator
            4. Fully peered: All nodes must be peered with all other nodes
            5. Crash fault tolerant: Raft does not provide Byzantine fault tolerance, only crash fault tolerance
## 10. Byzantine Fault Tolerance 
1. BFT Consensus in a Synchronous network for Safety and a Synchronous network for Liveness
    1. The FLP Impossibility works if network is asynchronous
    2. So if we assume our network is synchronous, we are free from the FLP Impossibility, and get both safety and liveness easily.
    3. But, as we saw above, network is asynchronous by nature.
    4. We cannot just assume that our network is synchronous because [hackers will attack](https://blockinpress.com/archives/16770) the time when our network becomes asynchronous, and since our consensus is not designed for asynchronous network, out consensus will be vulnerable to those hackers. 
    5. And we are doing consensus to guard our network against those hackers.
    6. So assuming our network is synchronous really is really stupid.
    7. But we can do a little bit better tho.
2. BFT Consensus in a Asynchronous network.
    1. Impossible to achieve both unlike BFT in a Synchronous Network : In a fully asynchronous system there is no consensus solution that can tolerate one or more crash failures even when only requiring the non triviality property by the FLP Impossibility.
3. BFT Consensus (Asynchronous: Safety, Synchronous(or Partial): Liveness)
    1. Partial here means that we can send messages within a bounded time, say t which is not infinity. Or, if messages are not sent and delivered within the time t, we can fix the network to work again.
    2. Let’s try this case.
    3. First we need to secure safety and liveness by definition to prove our network is safe from hackers and malicious byzantine nodes.
    4. Safety is easy to achieve whether a network is synchronous or asynchronous. So let’s assume our network is asynchronous when it comes to safety. And say we got safety because it is easy.
    5. Then by the FLP Impossibility -> we never get Liveness in the asynchronous network.
    6. Q: But then, how to get Liveness which is impossible? 
    7. A : So for liveness, assume our network is synchronous(or partials). Then, we can get liveness.
    8. So at least, we upgraded our consensus to guarantee safety even though our network is asynchronous when it comes to safety.
    9. However, since we need liveness, we have to assume that our network is synchronous(partial) anyway. 
    10. Examples 
        1. [PBFT](http://pmg.csail.mit.edu/papers/osdi99.pdf) (Asynchronous (safety)-- Synchronous (liveness))
        2. [Facebook’s LBFT](https://developers.libra.org/docs/assets/papers/libra-consensus-state-machine-replication-in-the-libra-blockchain.pdf) (partial synchronous network)
    11. In reality, assuming that a network is partially synchronous is not a stretch.
        1. But [hackers can still leverage this imperfection](https://blockinpress.com/archives/16770). 
            1. [Is Stellar As Secure As You Think](https://sites.google.com/view/stellar-analysis)
            2. [Safety vs. Liveness in the Stellar Network](http://www.scs.stanford.edu/~dm/blog/safety-vs-liveness.html)
        2. The FLP result does not state that consensus can never be reached: merely that under the model's assumptions, no algorithm can always reach consensus in bounded time. In practice it is highly unlikely to occur [9].
## 11. [PBFT](http://pmg.csail.mit.edu/papers/osdi99.pdf)
1. [Practical Byzantine Fault Tolerance](http://pmg.csail.mit.edu/papers/osdi99.pdf) by Miguel Castro and Barbara Liskov at MIT
2. Asynchronous(safety) + Synchronous(liveness, to be beat the FLP Impossibility)
3. Proved by the same team : [A Correctness Proof for a Practical Byzantine-Fault-Tolerant Replication Algorithm](https://cs.nyu.edu/courses/fall18/CSCI-GA.3033-002/papers/pbft-proof.pdf).
4. Provides high-performance Byzantine state machine replication, processing thousands of requests per second with sub-millisecond increases in latency [5].
5. Assumptions
    1. Assume that every node knows public keys of all nodes in the cluster
    2. Assume that the network is Asynchronous.
    3. Properties of Asynchronous network
        1. Assume that every node knows public keys of all nodes in the cluster 
        2. Assume that the network is Asynchronous. 
        3. Properties of Asynchronous network
            1. Message delay exists
            2. Message delivery may fail
            3. The same message may be sent twice
            4. Messages may arrive in out-of-order
            5. However, this paper does not assume a perfect asynchronous network. That is because even one node(server) is dead, then, consensus is impossible in the perfect  asynchronous network  by the FLP Impossibility. This paper does not  assume that message may not be delivered for a very long time, and that  engineer can fix the network if it has a delay problem so that a client  can get response eventually.
                1. Perfect Asynchronous
                    1. There is no unified clock for all processes.
                        1. Hence, Any algorithm that is using timeout cannot be used.
                2. There is no way to decide whether a process is running slow or the process is dead.
            6. Presence of byzantine nodes 
            7. This paper assumes that servers are independent, that is, a failure of one server does not affect failures of the other servers. Every node has its own different root password which prevents different networks getting intertwined.
            8. This paper assume that the network is using a strong asymmetric key that a server can never know signatures of other servers.
6. How PBFT Works
    1. in English : [Introduction to PBFT](https://www.hyperledger.org/blog/2019/02/13/introduction-to-sawtooth-pbft)
    2. in Korean : 
        1. [Consensus over Byzantine Fault (2) - PBFT(1)](https://suckzoo.github.io/tech/2018/02/19/bft-2.html)
        2. [Consensus over Byzantine Fault (3) - PBFT(2)](https://suckzoo.github.io/tech/2018/02/22/bft-3.html)
7. Message-types :
* <REQUEST, o, t, c>σ<sub>c<sub>
* <REPLY, v, t, c, i ,r>σ<sub>i<sub>
* <<PRE-PREPARE, v, n, d>p, m>
* <PREPARE, v, n, d, i>σ<sub>i<sub>
* <COMMIT, v, n, D(m), i>σ<sub>i<sub>
* <CHECKPOINT, n, d, i>σ<sub>i<sub>
* <VIEW-CHANGE, v + 1, n, C, P, i>σ<sub>i<sub>
* <NEW-VIEW, v + 1, V, O>σ<sub>p<sub>

8. The [RFC(Request for CommentsS) describing a practical Byzantine fault tolerant (PBFT) consensus algorithm for Hyperledger Sawtooth](https://github.com/hyperledger/sawtooth-rfcs/blob/master/text/0019-pbft-consensus.md)
    1. The PBFT algorithm is also inherently [crash fault tolerant](https://stackoverflow.com/questions/56336229/byzantine-fault-tolerance-bft-and-crash-fault-tolerance-cft). 
    2. Another advantage of PBFT is that blocks committed by nodes are final, so there are no forks in the network (unlike PoS’s Nothing at Stake Problem). This is verified by a "Consensus Seal," which is appended to blocks when they are finalized and checked upon receipt of a new block. The Seal consists of votes(signatures) of validators of the block [10].
    3. In the future, this base PBFT algorithm could be extended to other PBFT-style algorithms, which decrease the number of necessary nodes in the network and reduce the total number of inter-node communication steps required [10]
9. Most of BFT consensuses are based on Raft and PBFT.
    1. Ethereum 2.0’s [Casper](https://blockgeeks.com/guides/ethereum-casper/) (and PoS)
    2. [Hyperledger Fabric](https://hyperledger-fabric.readthedocs.io/en/release-1.4/network/network.html)
    3. [LFT by ICONLOOP](http://docs.icon.foundation/en/whitepaper/_static/LFT.pdf)
    4. [LBFT by facebook](https://developers.libra.org/docs/assets/papers/libra-consensus-state-machine-replication-in-the-libra-blockchain.pdf)
    5. Like everything.
10. Drawbacks
    1. PBFT also requires a large number of consensus-specific messages; the general PBFT algorithm requires five per published block, and this implementation requires three (because it does not directly interact with clients  [10]
    2. Additionally, PBFT does not prevent nodes from "leaking" information to bad actors [10]
    3. Perhaps the most significant drawback of this algorithm stems from a lack of information provided by the Consensus API. In order to be truly Byzantine fault tolerant, PBFT must have access to the ordering of batches inside of the block, not just the blocks themselves. Currently, the Consensus API does not provide any visibility about batches inside the blocks, so it can't be confirmed that all blocks indeed have the same batch list ordering. One possible solution to this would be to package the batch list inside the block. It is possible that the whole batch list is not necessary, perhaps a hash of it would be sufficient to ensure ordering of batches inside blocks provided by the Consensus API [10]
## 12. Ethereum 2.0
1. Ethereum 1.0 = PoW
2. [Ethereum 2.0](https://docs.ethhub.io/ethereum-roadmap/ethereum-2.0/eth-2.0-phases/) = PoS + BFT = Casper
3. [A Brief Summary of Ethereum 2.0 Yellow Paper](https://docs.google.com/document/d/1yE5Uuw5gxkoFD4y86qVjk18uk5QkHjwpciZTpRm-f0c/edit#) by Moonwon Lee @ berkeley.edu
## 13. [Hyperledger Fabric](https://hyperledger-fabric.readthedocs.io/en/release-1.4/network/network.html)
1. Permissioned blockchain
2. The Linux Foundation + IBM (+Intel, Samsung, ICONLOOP)
## 14. Nexledger by Samsung
## 15. [Libra by Facebook](https://libra.org/en-US/white-paper/)
1. based on [HotStuff: BFT Consensus in the Lens of Blockchain](https://arxiv.org/abs/1803.05069)


## References		
[1] Erik Zhang, [“Exploring Blockchain Consensus”,](https://docs.microsoft.com/en-us/archive/msdn-magazine/2019/october/blockchain-exploring-blockchain-consensus) 2019.

[2] Sohn Ji-young, [“Samsung SDS introduces new blockchain platform Nexledger”](http://www.theinvestor.co.kr/view.php?ud=20170406000977), 2017.

[3] Jimi S., "[Blockchain explained: how a 51% attack works (double spend attack)](https://blog.goodaudience.com/what-is-a-51-attack-or-double-spend-attack-aa108db63474)”, 2018.

[4] Alexandra Tran, “[A Cursory Introduction to Byzantine Fault Tolerance and Alternative Consensus](https://medium.com/@ancapalex/a-cursory-introduction-to-byzantine-fault-tolerance-and-alternative-consensus-1155a5594f18)”, 2017.

[5] Wikipedia, “[https://en.wikipedia.org/wiki/Byzantine_fault](https://en.wikipedia.org/wiki/Byzantine_fault)”.

[6] Miguel Castro and Barbara Liskov, [“Practical Byzantine Fault Tolerance”](http://pmg.csail.mit.edu/papers/osdi99.pdf), 1999.

[7] David Mazières ,“[https://www.scs.stanford.edu/~dm/blog/safety-vs-liveness.html](https://www.scs.stanford.edu/~dm/blog/safety-vs-liveness.html)”, 2019.

[8] Yutelin ,“[https://github.com/ethereum/EIPs/issues/650](https://github.com/ethereum/EIPs/issues/650)”, 2017.

[9] Bisping, Benjamin; et al. , Blanchette, Jasmin Christian; Merz, Stephan (eds.), _Mechanical Verification of a Constructive Proof for FLP_, 2016

[10] Logan Seeley, “[https://github.com/hyperledger/sawtooth-rfcs/blob/master/text/0019-pbft-consensus.md](https://github.com/hyperledger/sawtooth-rfcs/blob/master/text/0019-pbft-consensus.md)”, 2019.

[11] Logan Seeley, “[https://www.hyperledger.org/blog/2019/01/11/floating-the-sawtooth-raft-implementing-a-consensus-](https://www.hyperledger.org/blog/2019/01/11/floating-the-sawtooth-raft-implementing-a-consensus-algorithm-in-rust)

[algorithm-in-rust](https://www.hyperledger.org/blog/2019/01/11/floating-the-sawtooth-raft-implementing-a-consensus-algorithm-in-rust)”, 2019.

[12] Leslie Lamport, “[http://lamport.azurewebsites.net/pubs/web-byzpaxos.pdf](http://lamport.azurewebsites.net/pubs/web-byzpaxos.pdf)”, 2011.

[13] Lesile Lamport, “[http://lamport.azurewebsites.net/pubs/disc-leaderless-web.pdf](http://lamport.azurewebsites.net/pubs/disc-leaderless-web.pdf)”, 2011.
