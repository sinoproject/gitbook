# FAQ

### Can the owner inflate SINO token supply?

Nope. After the initial deployment and minting of the SINO token contract, its ownership was transferred to the Sino betting contract. Which is programmed to only mint/burn during bet placing/settling.

### Will tokenomics generate a constant rate of deflation?

Nope. Any system based on probabilities is subject to short term variance. Think about the following. If you operate a brick and mortar casino and on certain days you only get 10 customers playing your games, your profit/loss in those days depends on the luck of these customers and their bet amounts.&#x20;

Maybe winning customers on a given day are mostly high rollers betting $1000 per spin, while losing customers are mostly small time players betting $1 per spin. You won't make a profit in days like that. However, casinos (including Sino) know that, given a large volume of bets, the mathematical house edge will play out. So, Sino's tokenomics will play out over time if there's a large amount of bets placed.

### How reliable is the off chain random number generation?

Currently, the random number gets generated using a Javascript library called "crypto" which has a function called "randomInt". It is considered cryptographically secure, ensuring the randomness is unpredictable and difficult to guess. Also, all generated random numbers are auditable on chain as they are present inside BetSettled events emitted by the Sino betting contract.
