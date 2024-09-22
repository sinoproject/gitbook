# Creating Games

Anyone can create single-spin betting games on top of the Sino betting smart contract. It boils down to creating a web application that, on behalf of the gambler does the following:

* Call the Sino betting contract's **placeBet** function to place a bet.
* Note down the transaction hash.
* Listen for **BetPlaced** events emitted by the contract. When one is emitted for that transaction hash, note down the **betId** value it contains**.**
* Listen for **BetSettled** events emitted by the contract. When one is emitted for that **betId**, note down the following values it contains: **isWon, mintToBettor, jackpotAmountWon, updatedBettorTokenBalance**.
* Based on the above, play a winning/losing animation to the gambler, show them how much they won, their updated balance, etc.

You can view an HTML/Javascript coding example of the above in the code repository:\
[https://github.com/sinoproject/main/blob/main/webapp\_example/index.html](https://github.com/sinoproject/main/blob/main/webapp\_example/index.html)

### Caveats regarding placeBet

* Before calling it, you must call the Sino betting contract's **randomizerCallbackFee** function, which tells you how much ETH you should send as part of **placeBet** to cover the costs of the future bet settling transaction.
* When calling **placeBet**, you can also specify the **agent** parameter, basically your own wallet address: you will get sent a SINO token commission if the bet wins.
