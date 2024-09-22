# Auditability

Bet placing and settling are blockchain transactions. Sino smart contracts emit events during these transactions. These events are useful to listen to if you're building a web app with games on top of it.

But they also make Sino transparent and auditable. The following are the main events emitted, check the actual contract source code in the code repository for more details.

Sino betting contract events:

* BetPlaced
* BetSettled
* JackpotWon
* SettingsChanged

Sino randomizer contract events:

* RequestReceived
* RequestFulfilled
