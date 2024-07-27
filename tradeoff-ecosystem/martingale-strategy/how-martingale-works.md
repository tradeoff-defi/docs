# 🛞 How Martingale Works

Previously, we introduced what the Martingale strategy is and its execution conditions: unlimited funds, absence of malicious behavior, and a sufficiently large market size.

## **🔑 Solution:**

* **Liquidity Pool Approach:** By leveraging the market aggregation effect, the funds of various investors are pooled together, achieving the effect of unlimited funds.
* **Smart Contract Deployment:** The code is deployed as a smart contract on the blockchain. Due to the immutable nature of blockchain technology, smart contracts are highly binding, and transactions are secure and transparent.
* **24/7 Market:** The product optimizes cryptocurrency investment strategies, with cryptocurrencies being traded 24/7 and the global market volume reaching trillions of dollars, ensuring a sufficiently large market capacity.
* **Historical Analysis:** Analysis of historical trends of quality cryptocurrencies like BTC shows that users can profit using the Martingale strategy regardless of the purchase price. This strategy doubles investments when cryptocurrencies decline, effectively lowering the average entry price and profiting from price rebounds.

### ⚙️ Operational Logic

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Martingale leverages the power of market aggregation by increasing BTC positions during economic downturns to strictly adhere to the Martingale strategy. This process aims to bring the average purchase price of BTC in the Martingale pool closer to the current market price of BTC, ultimately achieving profitability. Please refer to the diagram below:\


<figure><img src="../../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>

#### **User Actions:**

* **Creating/Joining Pools:** When users create or join a pool, the smart contract utilizes Chainlink/Pyth to fetch the current market price of BTC and record it as the cost price. If BTC's price falls below a user-defined threshold, the pool will open for other participants to contribute their BTC. Oracles read the contributed BTC price and store it in the smart contract. However, the amount contributed cannot exceed the predetermined multiplier of the first layer, as shown in the diagram.
* **Accumulation During Downturns:** As more BTC at lower cost prices are added to the pool, the average cost of BTC in the pool steadily declines. The Martingale strategy results in this average cost reduction by adding more BTC to the pool at lower prices during price drops. Thus, the pool's average cost price gradually aligns with BTC's current market price, leading to profitability when BTC prices rebound.

### 💸 Profit Distribution

When the current market price of BTC exceeds the pool's profitable price, the pool achieves profitability. This means that at settlement, the value of BTC in the pool surpasses the total cash contributions from all users in the pool, generating a proportion of profit. Therefore, upon reaching an agreement, BTC in the pool is categorized into cost and profit, covering all users' contributions and generating profit.

The profit is divided into three parts:

* **Creator:** 5%
* **Ecosystem Fee:** 10%
* **Users:** 85%

<figure><img src="../../.gitbook/assets/image (2) (1) (1).png" alt=""><figcaption></figcaption></figure>

### 🏆 Winner mechanism

The winner mechanism is used to distribute the Winner Ratio's profit through a process as illustrated, with the final winner range fixed within the last 50% of the final layer's funds.

#### **Purpose:**

* **As a Pool Creator:** You can create a pool by purchasing cryptocurrencies at any price. If the price rises, the earnings from holding the cryptocurrency are not reduced. If the price falls, you can significantly lower your average holding cost through the pool's aggregated power, acquiring more cryptocurrencies without additional investment, thus reducing the risk associated with cryptocurrency investments.
* **As a Pool Joiner:** You can choose and join any pool at any time. If you join a pool nearing settlement, you can gain substantial returns. If cryptocurrency prices fall after joining, you will accumulate more cryptocurrencies like the creator during the subsequent decline, ensuring the cash value of your investment remains constant. This presents a highly profitable investment opportunity.

### 🧮 Settlement Formula

When the pool reaches the predetermined profit price, it switches to the "End" state. The specific settlement formulas are as follows:

<figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

**Note:** Node and referrer rewards account for 5% of the pool profit, calculated based on the proportion of lower-level earnings.

### User Relations

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>



### **Martingale Asset Status:**&#x20;

Users can usually withdraw crypto assets at any time in the Martingale protocol. After successfully creating a pool, it will undergo three states: "Open," "Closed," and "Ended."

**🔛"Open" State:**

* Triggered by asset price. When the market price is ≤ the opening price of the last layer, the pool switches to "Open," allowing current pool joining. During the "Open" state, all users except the last layer can withdraw assets, and settlement follows two methods:
  * **Cost Price ≥ Average Price:** Users can withdraw the number of assets they contributed.
  * **Cost Price < Average Price:**&#x20;

$$
Redeem=Input Price×AmountAverage Price\text{Redeem} = \frac{\text{Input Price} \times \text{Amount}}{\text{Average Price}}Redeem=Average PriceInput Price×Amount​
$$

**📴 "Closed" State:**

* Triggered by asset price or quantity. When the market price > the opening price of the last layer or the asset quantity of the last layer reaches the capacity threshold, the pool switches to "Closed," disallowing new joins. During the "Closed" state, all users except the last layer can withdraw assets, and settlement follows two methods:
  * **Cost Price ≥ Profit Price:** Users can withdraw the number of assets they contributed.
  * **Cost Price < Profit Price:**&#x20;

$$
Redeem=Input Price×AmountProfit Price\text{Redeem} = \frac{\text{Input Price} \times \text{Amount}}{\text{Profit Price}}Redeem=Profit PriceInput Price×Amount​
$$

In any state, tokens deducted due to subjective withdrawal will be used to lower the average price of the entire pool.

**Note:** Any withdrawal action, as long as the pool is not in the "Ended" state, will cause the pool's average price to decrease, which is beneficial for users choosing to continue participating in the pool.

**🔚 "Ended" State:**

* Triggered by asset price and user consensus. When the market price ≥ profit price and triggered by the frontend or contract, the pool switches to "Ended," allowing all users to withdraw assets. The number of assets users can withdraw during the "Ended" state is distributed according to the "Settlement Formula."
