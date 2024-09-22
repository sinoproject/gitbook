# Random Number Bet Settling

As explained in the Tokenomics section, the Sino betting contract uses a random number to determine whether a bet is won.

This number must be generated off chain by an oracle and injected into the blockchain. Smart contract execution is deterministic so we cannot generate a random number on chain.

Here is what happens.

* When a gambler places a bet, the Sino betting contract asks the randomizer contract for a random number.
* The randomizer contract provides a unique request ID, which the betting contract also uses as the bet ID.
* Off chain there's an oracle, a software running 24/7 listening for these random number requests.
* When it sees a new request, the oracle generates a random number and starts a new blockchain transaction to inject it into the randomizer contract.
* Which in turn calls Sino betting contract's bet settling function.

### Bet Placing/Settling Are Two Separate Transactions

As you can see, bet placing and bet settling are two different blockchain transactions.

This means that someone has to pay the fee for the setling transaction that injects a random number on chain and settles the bet.

This is why, when placing a bet, the gambler must both:

* Tell the betting contract how many SINO tokens they are betting
* Send a small amount of ETH that gets forwarded to the oracle operator to cover the bet settling transaction fee.
