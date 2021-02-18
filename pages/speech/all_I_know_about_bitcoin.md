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

Bitcoin did not come from nothing. In fact, there were a few predecessors
who had tried and failed for two decades prior. Then, in 2008, came Bitcoin.

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
$1 to be worth 1,309.03 BTC. Nakamoto released the second version of the
software in December.

With an exchange rate established, it was only a matter of time until someone
attempted to make an actual purchase with Bitcoins. In May of 2010, it happened.
Florida-based programmer Laszlo Hanyecz sent 10,000 BTC to a London man in
exchange for two pizzas, valued at a total of $25. This still valued a single
Bitcoin as a fraction of a penny, but with a purchase made, intrigued parties
saw potential in the product. A couple of months later, Bitcoin's value finally
broke the penny threshold

A pivotal year for the exchange of Bitcoin, fittingly the first Bitcoin
exchanges popped up in 2010 as well - Bitcoin Market in February, and Mt. Gox
in July. Slush, the first mining pool, also mined Bitcoin successfully for the
first time that year. Mining pools are where several miners combine resources
to get Bitcoin. By November, the market cap for Bitcoin surpassed $1 million
for the first time.

Not that it was all ups for Bitcoin. Someone spotted a vulnerability in
Bitcoin's protocol in October that allowed for transactions without proper
verification and exploited it, generating 184 billion BTC. The transaction
was soon erased and the vulnerability fixed.

Steadily making gains in value after finally passing 1 cent threshold, in
February 2011 a major milestone occurred: 1 Bitcoin was worth $1 for the
first time.

Bitcoin began receiving press - both good and bad. TIME Magazine published an
article on Bitcoin for the first time, but the same year there was also an
article on Gawker detailing Silk Road, the dark web drug market where Bitcoin
was frequently used as payment. The publicity got people talking, and by June,
Bitcoin was worth over $30. Soon after, it crashed back down to about $10.

Also in June, Mt. Gox dealt with a serious security breach that compromised
tens of thousands of accounts and their Bitcoins. It would not be the first
security issue Mt. Gox would deal with.

Still, Bitcoin was becoming an entity that more and more of the public knew
about and interest in the cryptocurrency grew. This led to a rise in altcoins,
other forms of cryptocurrency whose developers were either trying to improve
upon Bitcoin or had created the digital coin for a different purpose. In 2011,
Litecoin -- now the seventh-largest cryptocurrency by market cap -- debuted.

If 2011 was a choppy year for Bitcoin, 2012 was smoother sailing. Among notable
moments for Bitcoin on its way to becoming the world's top digital coin was
its crossing the $100 threshold in April.

Bitcoin's price saw its share of ups and downs in 2013, but it passed a value
of $1,000 for the first time and was becoming the most recognizable and
successful wallet and exchange available.

And then... it stalled for a while. Quickly in January 2014 it fell below
$1,000 and struggled below the key level for a few years. A few things of
note happened, like Crypto exchange Mt. Gox going bankrupt and shutting down,
but this period mostly saw Bitcoin rising and falling somewhat while failing
to reach its high.

2017, though, was the biggest and busiest year for Bitcoin. After spending
2016 desperately trying to claw its way back up, 2017 was when it finally
reached and passed the $1,000 mark. It kept ascending. By June, Bitcoin was
worth over $3,000.

Still, some Bitcoin users were frustrated with the network around this time as
well. The rising number of Bitcoin miners meant higher fees and more time spent
processing transactions, leading some to want an increase in block size. In
August, this led to Bitcoin Cash (BCH) being created via a fork in the network.
Bitcoin Cash is now the fifth-largest cryptocurrency by market cap.

Until now, 2017 was considered the pivotal year for Bitcoin. The world’s first
and leading cryptoasset continued gaining legitimacy among lawmakers, financial
institutions, and retail companies, further legitimizing crypto in the
mainstream. Bitcoin underwent a hard fork on August 1st, splitting into Bitcoin
(BTC), and Bitcoin Cash (BCH). At the pinnacle of its historic bull run that
year, Bitcoin’s price reached an all-time high of over $20,000 USD.

Still, for the remainder of 2017 Bitcoin was on an upswing. By October, it was
topping $6,000. It ended November at nearly $10,000, and by the end of December
Bitcoin hit a peak of $19,783. More and more people and companies began chasing
the trend as the price just kept rising. Unsurprisingly, it wouldn't continue
that heady growth.

2018 has been a rough year for Bitcoin users, especially ones who held on
assuming the price would keep ascending. Many sold their Bitcoins while they
could, and the price has steadily dropped all year. As of this writing,
Bitcoin's price is at $6,542.78, a decline of 67%.

Despite a number of setbacks and recoveries, true crypto believers continued
to “HODL,” never doubting the day when Bitcoin would rise again. The last
few months of 2020 seem to mark yet another very important point in
Bitcoin’s history. As we continue to watch the events unfold, it seems safe
to say that Bitcoin’s 12th birthday celebration is a happy one indeed.

The world’s first cryptocurrency, Bitcoin is stored and exchanged securely
on the internet through a digital ledger known as a blockchain. Bitcoins
are divisible into smaller units known as satoshis — each satoshi is worth
0.00000001 bitcoin.

The entire principle of Bitcoin was to build a trustless network that is immune
to corruption and censorship. By effectively cutting out the intermediary in a
transaction, Bitcoin renders the banks obsolete and can provide a level of
security that the current systems cannot.

What makes Bitcoin and other cryptocurrencies so effective is that they have no
central point of failure. Thousands of nodes maintain Bitcoin’s blockchain
across the globe, so even if one node goes down, the network continues to run
smoothly on others.

Our current financial system and the Internet itself are still based on a
centralized network, meaning that if the central hub of the network is
compromised, everything around it ceases to function. This is how Bitcoin
has survived, despite multiple attacks on it.

This solution came at a time when the world was financially on the brink
of ruin. For decades, institutional money has enjoyed first-mover advantage
in investing and compounding wealth, usually long before the average
investor has a chance to lock his position.

Cryptocurrencies are the road that goes in the opposite direction, enabling
us to fully reclaim any lost purchasing power we incurred over the years.

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

Mt. Gox Hacks

At one point in Bitcoin's history, it could be argued that Mt. Gox, a
Tokyo-based Bitcoin exchange, was the largest exchange. But by 2014, it was
gone.

Mt. Gox was plagued with security issues that would become its downfall. The
2011 hack came just a few months after Mark Karpelès, a French businessman,
purchased the exchange. The hacker, upon access, artificially altered the
nominal value of Bitcoin all the way down to one cent and then transferred
2,000 BTC from Mt. Gox customer accounts onto the exchange. These Bitcoins
were sold, and in the brief moment that Bitcoin appeared to be worth a single
penny, 650 were purchased.

This was a brief but severe setback for Mt. Gox, but the exchange put in new
security measures and stabilized, growing to the biggest exchange by 2013.
These security measures, though, weren't as effective as they had hoped. In
early February of 2014, Mt. Gox stopped Bitcoin withdrawals. A few weeks
later, all trading was stopped.

As it turned out, Mt. Gox was being hacked for years. Overall, hackers had
taken 100,000 Bitcoins from the exchange - and over 744,000 from Mt. Gox
customers. The company was insolvent, and the exchange filed for bankruptcy
protection.

It's possible you only heard about Bitcoin in the last couple of years, but
cryptocurrency developed a passionate following even when it was smaller.
Some of those passionate people also took umbrage with some elements of
Bitcoin, and others thought the blockchain behind it could be used for other
purposes.

Bitcoin is still the cryptocurrency with the largest market cap by a large
margin. Previously mentioned other altcoins (Litecoin, XRP, Bitcoin Cash)
are also in the top 10. In second is Ethereum and its cryptocurrency of Ether.
Ethereum stands out from others because its blockchain is used to hold data
like smart contracts.

Thank you.