---
title: A Blockchain Primer by way of a Bad Metaphor
image: "blockchain-primer.jpg"
subTitle: This is the start of a series of posts that I plan to do on how to build up a block chain from first principals.
---
In this series of Blockchain from first principals, I am going to build up the knowledge required to build a blockchain from the maths you learned in High School.

Before we even start looking at what a blockchain is, we need to know what problems it is trying to solve. To answer this question, let's look at one of the first and still most popular Blockchains, Bitcoin.

The inventor of bitcoin, [Satoshi Nakamoto](https://en.wikipedia.org/wiki/Satoshi_Nakamoto), wanted to create a currency that could not be controlled by a single entity (decentralised), like a government or bank, and that anyone could participate in (peer to peer). The problem with this is that if there is no central authority that controls the currency, how do you trust anyone in the network. Someone could for example spend the same bitcoin twice (double spend), or they could spend more bitcoin than they own, or they may say that they have sent you bitcoin, but have not.

Let's break that down a little more:  
**Decentralised:** means that there is no central authority that controls the network. There is no company that a government can compel to shut down Bitcoin because not one owns it. As long as there are nodes in the network, bitcoin will continue to exist.  
**Peer to Peer:** means that there is a network of peers, or in Bitcoin speak, nodes, that all communicate with each other. A not is just a computer that is running the bitcoin software. Any node can talk to any other node and all nodes are equal.  

In order for this to work, we need a way for all the nodes to agree about what has happened and write them to the Block chain. When we are talking blockchain, this is called consensus. Lets use an example: Suppose you go to a gathering and you meet a some people that you have never met before. There are no ATM's around, so you all decide to pool all the cash and share the pot. You have no Idea about how much each of you are putting into the pot, and no one is appointed as the record keeper. Bob says that he put $100 into the pot but Eve says that he only put $50 in. How would you settle this dispute? You would ask other people right? This is exactly how Bitcoin works. Each node batches up the transactions into blocks and adds them to the end of the previous block and thus creating a chain. If the nodes do not agree with the block that has just been added, it is called a fork. To resolve this fork, the nodes "vote" for the fork that they trust by added their blocks to the end of the chain they trust. This way the longest for becomes the most trusted chain, in the same way as the more people that say Bob put $100 in, the more that becomes the trusted information.

But what happens if Eve decides to recruited all her friends to say that Bob put $50 in? How do we stop people from lying for Eve? Bitcoin uses a process called "Proof of Work" or "Mining". Lets say that in order to vote on how much each person put in, we gave each person the same puzzle to solve. The first person to solve the puzzle gets to cast their vote, and gets $1 as a reward. This way there is no guarantee that Eve's friends will get to vote, and the incentive is not to cheat, because if you lie, you loose the $1 reward when the next few votes come in. I will dig into mining in much more depth later on in this series.

There is another mechanism called "Proof of Stake", that Etherium uses, to keep everyone honest. In our example, we decide that if anyone is caught lying, then they lose all the money that they put in the pot. The votes are handed out randomly and the more mony that you put in the pot, the more likely you will be picked to vote because you have more to loose. I will also be digging into this topic further.

So in our example we have a decentralized system (Nether Bob nor Eve controls the system), any one can participate, we have a mechanism to resolve disputes and we have a way to motivate people to be honest. It is not a perfect metaphor for Bitcoin, non ever are, but it gets the basic concepts across.
