# 💸 Martingale Reward Mechanism

## Reward Distribution Rules

To incentivize user participation in liquidity pools, the platform releases a certain amount of tokens (TRO) daily as rewards, distributed based on users' contributions in various pools.

### Overall Reward Distribution

The total amount of tokens released daily is RdailyR\_{\text{daily\}}Rdaily​. Each pool receives tokens based on its liquidity value (in USD) proportionate to the total liquidity value across all pools.

The reward for each pool is calculated as follows:

$$
Rpooli=Vpooli∑j=1nVpoolj×RdailyR_{\text{pool}_i} = \frac{V_{\text{pool}_i}}{\sum_{j=1}^{n} V_{\text{pool}_j}} \times R_{\text{daily}} Rpooli​​=∑j=1n​Vpoolj​​Vpooli​​​×Rdaily​
$$

Where:

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

### In-Pool Reward Distribution

The rewards for each pool are distributed as follows:

* **80% to users in the last layer.**
* **20% to users in other layers.**

### User Reward Calculation

User rewards within each pool are distributed proportionally based on the number of tokens provided.

#### Last Layer User Reward Calculation:

$$
Rlastij=Tlastj∑k=1mTlastk×RlastiR_{\text{last}_{ij}} = \frac{T_{\text{last}_j}}{\sum_{k=1}^{m} T_{\text{last}_k}} \times R_{\text{last}_i} Rlastij​​=∑k=1m​Tlastk​​Tlastj​​​×Rlasti​​
$$

Where:\


<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

#### Other Layers User Reward Calculation:

$$
Rotherij=Totherj∑k=1pTotherk×RotheriR_{\text{other}_{ij}} = \frac{T_{\text{other}_j}}{\sum_{k=1}^{p} T_{\text{other}_k}} \times R_{\text{other}_i} Rotherij​​=∑k=1p​Totherk​​Totherj​​​×Rotheri​​
$$

Where:

<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

#### Example

Assume the total daily token release is 100,000 TRO.

**Calculating Pool Rewards**

There are three pools, A, B, and C, with the following liquidity values:

| Pool | Liquidity Value (USD) |
| ---- | --------------------- |
| A    | 50,000                |
| B    | 30,000                |
| C    | 20,000                |

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

**Pool A's Reward Distribution**

Pool A's total reward is 50,000 TRO, distributed as follows:

* **Last Layer Users:** 40,000 TRO
* **Other Layers Users:** 10,000 TRO

Assume the following users in Pool A:

| User | Token Amount | Layer       |
| ---- | ------------ | ----------- |
| A1   | 1            | Other Layer |
| A2   | 2            | Other Layer |
| A3   | 3            | Last Layer  |
| A4   | 5            | Last Layer  |

**Last Layer Users Reward Distribution:**

<div align="left">

<figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

</div>

**Other Layers Users Reward Distribution:**

<figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

This distribution ensures that rewards are proportionally allocated based on the contributions of each user within the liquidity pools, encouraging more participation and liquidity provision.
