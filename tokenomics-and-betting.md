# Tokenomics And Betting

The Sino betting contract is designed to only accept bets placed with SINO tokens. When a bet is placed, the contract burns these tokens. When a bet is won, it mints tokens to pay the winner.

The amount of tokens minted on a winning bet is lower than probability implies. Over time this will generate more burning than minting, therefore **deflating the token supply**.

### How Betting Works

Let's say a gambler bets 1000 SINO with a chosen 2x payout, basically betting at decimal odds of 2.00 First the Sino betting contract burns the user's 1000 SINOs then asks an oracle for a random number.

In a separate transaction, when the random number gets injected to chain, the Sino betting contract performs the following calculations.

* It determines the bet's implied winning probability, in this case 50% (basically 100% divided by 2.00).
* It applies the 2% house edge, giving this bet a 49% winning chance instead of 50%. In this case, the bet will be deemed a winner if the random number is between 1 and 4900 (out of a max 10000).
* If the bet is a loser then nothing else happens.
* Let's say this bet is a winner. The contract mints 2000 SINOs and transfers it to the gambler's wallet, who gets their chosen payout.
* Then it calculates the fair payout based on the 49% winning chance, which is 2040 SINOs (1000 \* (100 / 49)).
* Of these extra 40 SINOs: 10 get minted and sent to the bet agent, 10 get minted and added to the jackpot fund, **20 never get minted and this is the deflation in action**.

### House Edge Over Several Bets

Now let's apply the above to a hypothetical 100 bets of 1000 SINOs at odds of 2.00, of which on average 49 will be winners:

* 100,000 SINOs burned
* 98,000 SINOs minted to the winner
* 490 SINOs minted to agents
* 490 SINOs minted to jackpot fund
* Net burn: 1020 SINOs

Basically the gambler wins their chosen payout, but slightly less frequently than the odds imply. This allows the tokenomics to: deflate the token, reward agents, incentivise more betting by increasing the jackpot fund.

