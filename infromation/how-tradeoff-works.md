# 💹 How TradeOFF Works

In the [previous section,](martingale-strategy.md) we learned about the Martingale strategy and the conditions necessary for executing it: unlimited funds, no malicious behavior, and a sufficient market size.

## 📈 TradeOFF Solutions

* **Unlimited Funds**: TradeOFF employs liquidity mining, leveraging market aggregation to pool funds from other investors, achieving the effect of unlimited funds.
* **Security and Transparency**: TradeOFF deploys its code as smart contracts on the blockchain. The inherent characteristics of blockchain technology (immutability) ensure that smart contracts are highly enforceable, and transactions are transparent and secure.
* **Sufficient Market Size**: TradeOFF optimizes cryptocurrency investment strategies. Cryptocurrencies are traded 24/7, with a daily trading volume in the trillions of dollars, ensuring a sufficiently large market.

### &#x20;▶ Operating Logic

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

Through historical analysis of premium cryptocurrencies like BTC, it has been found that users can profit by applying the Martingale strategy regardless of the purchase price. This strategy takes advantage of doubling down on investments during price drops, effectively lowering the average entry price and profiting from price rebounds.

TradeOFF harnesses the power of market aggregation to rigorously adhere to the Martingale strategy by increasing BTC positions during economic downturns. The aim is to bring the average purchase price of BTC in the TradeOFF pool closer to the current market price of BTC, ultimately achieving profitability.

Please refer to the diagram below for further illustration.

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

When a user creates or joins a pool, the smart contract fetches the current market price of BTC using Chainlink/Pyth and records it as the initial price. If BTC’s price drops below a user-defined threshold, the pool opens for other participants to add their BTC. The oracle reads the BTC price and stores it in the smart contract. The quantity added cannot exceed the predetermined multiple of the first layer, as illustrated above.

As more lower-cost BTC is added to the pool, the average cost of BTC in the pool steadily decreases. This reduction in average cost results from the Martingale strategy, which involves adding more BTC to the pool at lower prices during price drops. Consequently, the pool’s average cost approaches the current market price of BTC, achieving profitability when BTC prices rebound.

### 💰Profit Distribution

Based on the description above, we can conclude that the pool becomes profitable when the current market price of BTC exceeds the pool’s settlement price. This means that at settlement, the value of BTC in the pool surpasses the total cash input from all users in the pool, generating a proportionate profit. Once the agreement is reached, we categorize the BTC in the pool into two types: cost and profit. This includes all user inputs in the pool, generating a profit.

As shown in the diagram, the profit is divided into five parts:

* Winners: 70%
* Creators: 10%
* Nodes: 5%
* Ecosystem fee: 10%
* Referrer: 5% (if no referrer, this part will be considered as an ecosystem fee)

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

When the pool reaches the predetermined settlement price, it switches to the "settlement" state. All participants can then withdraw their assets based on the cost price at which they were added to the pool.

The formula for calculating the settlement amount is: **Settlement Amount = Initial Price \* Initial Quantity / Settlement Price**

### 🏆 Winner Mechanism

TradeOFF uses the Martingale strategy to aggregate market liquidity and generate additional profits. 70% of these profits are distributed through the winner mechanism. As shown in the diagram, the final winner range is fixed within the last 50% of the final layer.

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

### ⚙️ Purpose of the Distribution Mechanism

* **As a Pool Creator**: You can create a pool at any time using cryptocurrency purchased at any price. If the cryptocurrency's price rises, your gains are preserved. If the price falls, the power of market aggregation significantly reduces your average holding cost, allowing you to acquire more cryptocurrency without additional investment. This effectively reduces the risks associated with cryptocurrency investment, making it a much more stable option.
* **As a Pool Participant**: You can choose and join any pool at any time. If you join a pool that is close to settlement, you stand to gain substantial returns. If the cryptocurrency's price drops after joining, like the creator, you accumulate more cryptocurrency during the subsequent decline, ensuring that your invested cash value remains stable. This presents a highly profitable investment opportunity.

## Asset States in TradeOFF

In the TradeOFF protocol, users can usually withdraw their crypto assets at any time. Once a pool is successfully created, it goes through three states: "Open," "Closed," and "Settlement."

### 🔛 "Open" State

Triggered by asset price, the pool switches to "Open" when the spot price is less than the opening price of the last layer. In this state, users can join the pool, and all users, except those in the last layer, can withdraw assets with two settlement methods:

* If the initial price when joining is greater than or equal to the pool's average price, the withdrawable asset amount is the initial quantity.
* If the initial price when joining is less than the pool's average price, the withdrawable asset amount is calculated as the initial price \* initial quantity/pool's average price.

### 📴 "Closed" State

Triggered by asset price or quantity, the pool switches to "Closed" when the spot price is greater than the opening price of the last layer or when the last layer's asset quantity reaches the capacity threshold. In this state, users cannot join the pool, but all users except those in the last layer can still withdraw assets with two settlement methods:

* If the initial price when joining is greater than or equal to the settlement price, the withdrawable asset amount is the initial quantity.
* If the initial price when joining is less than the settlement price, the withdrawable asset amount is calculated as the initial price \* initial quantity/settlement price.

Any withdrawal in this state lowers the pool's average price, benefiting users who choose to remain in the pool.

### 🧮 "Settlement" State

Triggered by asset price and user action, the pool switches to "Settlement" when the spot price is greater than the settlement price, and someone triggers it via the front end or contract. In this state, all users can withdraw assets, with the withdrawable amount calculated as initial price \* initial quantity/settlement price.

Note: Any withdrawals in non-settlement states lower the pool's average price, benefiting continuing participants.
