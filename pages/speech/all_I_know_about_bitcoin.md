---
layout: page
title: All I know about Bitcoin
description: On 2021-02-21 gave this speech as I the level-1 project-5 of my Pathways in Yulife club of Toastmaster.
---


Dear Fellow members,
Distinguished guests,

Good morning.

Please look at the figure carefully. What does it reminder you?

This is the value of Bitcoin since its birth in 2008. It is a curve of
exponent.

```
1 Bitcoin = 50,000 USD
```

It's possible you only heard about Bitcoin in the last couple of years,
while Bitcoin did not come from nothing. In fact, there were a few
predecessors who had tried and failed for two decades prior. Then, in
2008, came Bitcoin.

In August of that year, Bitcoin.org was registered.
Two months later, On October 31st, a white paper was published:
"Bitcoin: A Peer-to-Peer Electronic Cash System."
This date can be viewed as Bitcoin’s conception.

Satoshi Nakamoto, an unknown person or group of people, wrote the Bitcoin
white paper. The document outlined the use of a peer-to-peer network
(a blockchain), to create a digital currency (cryptocurrency) that would
function independently of third parties such as banks or governments.

The white paper described the revolutionary vision of a decentralized digital
cash system: secure digital signatures, not requiring the use of a third party,
proof-of-work, and hashing the transactions together to form a chain.

Bitcoin Block structure Field | 	Description | 	Size
:-----------------------|:-----------------:|--------:
Magic no 	|value always 0xD9B4BEF9 |	4 bytes
Blocksize 	|number of bytes following up to end of block| 	4 bytes
Blockheader 	|consists of 6 items 	|80 bytes
Transaction counter| 	positive integer VI = VarInt| 	1 - 9 bytes
transactions 	|the (non empty) list of transactions |	<Transaction counter>-many transactions

Blockheader Field| 	Purpose| 	Updated when...| 	Size (Bytes)|
:----------------|:-----------:|:---------------------:|--------------------:
Version 	|Block version number| 	You upgrade the software and it specifies a new version| 	4
hashPrevBlock 	|256-bit hash of the previous block header 	|A new block comes in| 	32
hashMerkleRoot 	|256-bit hash based on all of the transactions in the block| 	A transaction is accepted| 	32
Time 	|Current block timestamp as seconds since 1970-01-01T00:00 UTC 	|Every few seconds 	|4
Bits 	|Current target in compact format| 	The difficulty is adjusted| 	4
Nonce 	|32-bit number (starts at 0) 	|A hash is tried (increments) 	|4

The Satoshi whitepaper came on the heels of 2008’s major financial crisis
shortly after the closure of Lehman Brothers, which rocked markets and
economies worldwide. The timing of this is not a coincidence. Bitcoin was
indeed launched as a solution for how we conduct payments.

It is actually January 3rd, however, that commemorates the `birth’ of the
world’s first cryptocurrency — the date on which Bitcoin officially came
into existence in the practical sense and was mined for the very first time.

On January 3rd, 2009, the Bitcoin blockchain became a reality, and
Satoshi Nakamoto mined the genesis block of Bitcoin (known as Block 0),
which had a reward of 50 BTC. SourceForge hosted the first open-source
Bitcoin client, released on January 9th, 2009, and three days later,
the world’s first Bitcoin transaction transpired, with Hal Finney,
one of Bitcoin’s earliest supporters, receiving 10 BTC from Satoshi Nakamoto.

Satoshi added a message to the genesis block’s coinbase parameter, which was
the headline of the British newspaper, “The Times,” on the day the first block
was mined.

The message was:
“The Times 03/Jan/2009 Chancellor on brink of second bailout for banks.”

This could be to prove the block was generated on January 3rd, 2009, or to
highlight Bitcoin being the solution to the global financial problems.

Toward the end of the year, in October, the New Liberty Standard publishes
the first Bitcoin exchange rate in the young cryptocurrency's history, deeming
$1 to be worth 1,309.03 BTC.

In May of 2010, Florida-based programmer Laszlo Hanyecz sent 10,000 BTC to a
London man in exchange for two pizzas, valued at a total of $25. A couple of
months later, Bitcoin's value finally broke the penny threshold.

Steadily making gains in value after finally passing 1 cent threshold, in
February 2011 a major milestone occurred: 1 Bitcoin was worth $1 for the
first time.

Bitcoin became the world's top digital coin when it crossed the $100
threshold in April, 2012. Bitcoin's price saw its share of ups and downs
in 2013, but it passed a value of $1,000 for the first time and was becoming
the most recognizable and successful wallet and exchange available.

In 2017 Bitcoin was on an upswing. By October, it was topping $6,000. It ended
November at nearly $10,000, and by the end of December Bitcoin hit a peak of
$19,783. More and more people and companies began chasing the trend as the
price just kept rising. Unsurprisingly, it wouldn't continue that heady growth.

2018 has been a rough year for Bitcoin users. The price has steadily dropped
all year to $6,542.78, a decline of 67%.

Despite a number of setbacks and recoveries, true crypto believers continued
to “HODL,” never doubting the day when Bitcoin would rise again. The last
few months of 2020 seem to mark yet another very important point in
Bitcoin’s history. As we continue to watch the events unfold, it seems safe
to say that Bitcoin’s 12th birthday celebration is a happy one indeed. We
see the curve in the beginning: 1 BTC = $50,000.

The entire principle of Bitcoin was to build a trustless network that is immune
to corruption and censorship. By effectively cutting out the intermediary in a
transaction, Bitcoin renders the banks obsolete and can provide a level of
security that the current systems cannot.

What makes Bitcoin and other cryptocurrencies so effective is that they have no
central point of failure. Thousands of nodes maintain Bitcoin’s blockchain
across the globe, so even if one node goes down, the network continues to run
smoothly on others. This is how Bitcoin has survived, despite multiple attacks
on it.

Bitcoin has been running no-stop for the past 12 years, used by tens of
millions of people, has a market cap of 1 Trillion and all that while
protecting the human rights around world.

I think it is a working proof of the concept of cryptocurrency and blockchain.

Thank you.



More information:

Bitcoins are divisible into smaller units known as satoshis — each satoshi
is worth 0.00000001 bitcoin.


What Is Bitcoin Mining?

Bitcoin mining is the process of creating new bitcoin by solving a computational
puzzle. Bitcoin mining is necessary to maintain the ledger of transactions upon
which bitcoin is based.

The result of bitcoin mining is twofold. First, when computers solve these
complex math problems on the bitcoin network, they produce new bitcoin (not
unlike when a mining operation extracts gold from the ground). And second, by
solving computational math problems, bitcoin miners make the bitcoin payment
network trustworthy and secure by verifying its transaction information.

When someone sends bitcoin anywhere, it's called a transaction. Bitcoin
miners clump transactions together in “blocks” and adding them to
a public record called the “blockchain.” Nodes then maintain records of
those blocks so that they can be verified into the future.

When bitcoin miners add a new block of transactions to the blockchain, part of
their job is to make sure that those transactions are accurate. In particular,
bitcoin miners make sure that bitcoin is not being duplicated, avoiding
double-spending.

In order for bitcoin miners to actually earn bitcoin from verifying
transactions, two things have to occur. First, they must verify one
megabyte (MB) worth of transactions, which can theoretically be as small
as one transaction but are more often several thousand, depending on how
much data each transaction stores.

Second, in order to add a block of transactions to the blockchain, miners must
solve a complex computational math problem, also called a "proof of work."
What they're actually doing is trying to come up with a 64-digit hexadecimal
number, called a "hash," that is less than or equal to the target hash.

What is Proof of Work?

Proof-of-work is the system Bitcoin's blockchain network uses to create and
hash blocks together. When the computer in a network must use proof-of-work
for mining, it needs to solve a complicated mathematical problem. If a
computer (called a "node" in the network) successfully solves the problem, it
must then be verified by the other nodes in the network. If it does, the
transaction is verified and completed, and the miner whose node solved it is
rewarded with Bitcoins.

Proof-of-work is an incredibly controversial method. It's a secure method of
verifying transactions, but requires a lot of energy. As more and more people
began mining bitcoins, more high-powered mining hardware and graphics
processing units (GPU) were created for people to gain an advantage. This
consumes large amounts of energy, and with so many Bitcoin and other
cryptocurrency miners out there, many are worried about the environmental
ramifications. Some cryptocurrencies are testing a proof-of-stake method,
which consumes significantly less power.

Who is Satoshi Nakamoto?

One of the most compelling aspects of Bitcoin is the mystery of who created it.
The only information the community has is someone (or some people) using the
alias Satoshi Nakamoto, who is responsible for creating Bitcoin, mining the
first block, and maintaining the network’s development in the very early days.

After a short length of time, Satoshi Nakamoto disappeared from the ongoing
development of Bitcoin and has not made any known attempt to make contact, nor
left any clues to his origin. This has resulted in the cryptocurrency community
regularly speculating as to who the mysterious persona is.

In 2009, mining Bitcoin had almost zero competition and it was a task that could
be done on a CPU. Many miners from 2009 sit on a fortune of Bitcoin, including
Satoshi Nakamoto.

Nakamoto owns around 1,000,000 Bitcoin from being one of the first miners. The
wallet has never been accessed to this day!

Satoshi Nakamoto is merely a pseudonym. The person behind it, however, remains
a mystery.

It remains such a mystery that some think it's more than one person, doubting
that one single person could create something as comprehensive as the Bitcoin
network. Still, others have floated the possibility of it being one person,
and there are plenty of theories as to who that one single person could be.
None have been verified.

Who are the people that some people think could be Satoshi? Some of them have
already been mentioned in this article, such as Bit Gold founder Nick Szabo,
whose ideas were remarkably similar to that of Bitcoin. Others think it may
have been Hal Finney, a notable developer and the person Nakamoto sent
Bitcoins to in the first ever Bitcoin transaction all the way back in 2009.

One person is speculated as Satoshi because he tried literally saying he was.
That person was Craig Wright, an Australian businessman who not only publicly
claimed to be Satoshi Nakamoto but promised he would provide proof of it. So
far, he has not provided this proof.