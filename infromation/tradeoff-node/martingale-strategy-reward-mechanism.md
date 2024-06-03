# 🎲 Martingale Strategy Reward Mechanism

#### Reward Mechanism Operational Logic

The LV Algorithm (Liquidity Value Algorithm) and POLE Engine (Proof of Liquidity Efficiency Engine) ensure fair distribution of rewards based on the amount of liquidity each user provides, the duration, market price, and the vToken ratio.

### LV Algorithm - Liquidity Value (LV) Algorithm

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

**Liquidity Value (LV) Calculation Formula**:

$$
LV[𝑖,cycle(𝑡)]=𝐴(𝑖)×Price(𝑖)×𝑇(𝑖)LV[i,cycle(t)]=A(i)×Price(i)×T(i)
$$

* _**cycle(t)**_: Each liquidity cycle.
* _**A(i)**_: Amount of liquidity.
* _**Price(i)**_: Liquidity price.
  * If the liquidity is inherited from the previous cycle, the price is the average price of the previous cycle _**Average Price(t−1)**_.
  * If it is newly added liquidity, the price is the input price of the liquidity _**Input Price of liquidity(i)**_.
* _**T(i)**_: Total time the liquidity is added during the cycle.

### POLE Engine - Proof of Liquidity Efficiency (POLE) Engine

<figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

* **vToken Reward Calculation Formula**:

$$
𝑉(𝑖,𝑡)=Mint(cycle[𝑡])×[LV(𝑖,𝑡)×𝑆(𝑖)]∑LV[𝑖,cycle(𝑡)]×𝑆(𝑖)V(i,t)=∑LV[i,cycle(t)]×S(i)Mint(cycle[t])×[LV(i,t)×S(i)]​
$$

* _**V(i,t)**_: vToken reward received by the user in a cycle.
* _**Mint(cycle\[t])**_: Number of vTokens minted in cycle _**t**_.
* _**S(i)**_: vToken ratio delegated by the user.

### Operational Process

1. Confirm the liquidity price _**Price(i)**_.
2. Calculate the liquidity value _**LV\[i,cycle(t)]**_.
3. Calculate the vToken reward _**V(i,t)**_.

### Example

Assume the following scenario in cycle _**t**_:

* User 1: Provides 10 BTC at $50,000 each, present every day, total time _**T(1)**_ is 30 days, vToken ratio _**S(1)**_ is 0.5.
* User 2: Provides 5 BTC at $55,000 each, present every day, total time _**T(2)**_ is 30 days, vToken ratio _**S(2)**_ is 0.3.
* User 3: Provides 2 BTC at $52,000 each, present every day, total time _**T(3)**_ is 30 days, vToken ratio _**S(3)**_ is 0.2.

### **Liquidity Value for Each User**:

$$
LV(1,𝑡)=10×50000×30=15,000,000LV(1,t)=10×50000×30=15,000,000
$$

$$
LV(2,𝑡)=5×55000×30=8,250,000LV(2,t)=5×55000×30=8,250,000
$$

$$
LV(3,𝑡)=2×52000×30=3,120,000LV(3,t)=2×52000×30=3,120,000
$$

### **Total Liquidity Value**:

$$
∑LV[𝑖,𝑡]×𝑆(𝑖)=15,000,000×0.5+8,250,000×0.3+3,120,000×0.2=7,500,000+2,475,000+624,000=10,599,000∑LV[i,t]×S(i)=15,000,000×0.5+8,250,000×0.3+3,120,000×0.2=7,500,000+2,475,000+624,000=10,599,000
$$

### Calculating vToken Rewards

Assume the total number of vTokens minted is 100,000

* **User 1**:

$$
𝑉(1,𝑡)=100,000×15,000,000×0.510,599,000≈70,805V(1,t)=10,599,000100,000×15,000,000×0.5​≈70,805
$$

* **User 2**:

$$
𝑉(2,𝑡)=100,000×8,250,000×0.310,599,000≈23,407V(2,t)=10,599,000100,000×8,250,000×0.3​≈23,407
$$

* **User 3**:

$$
𝑉(3,𝑡)=100,000×3,120,000×0.210,599,000≈5,887V(3,t)=10,599,000100,000×3,120,000×0.2​≈5,887
$$

## Summary

* **Balancing Market Performance**: The algorithm ensures that liquidity providers are fairly rewarded during market fluctuations by considering the market performance (price) of liquidity over different periods.
* **Time Factor**: The total time liquidity is present during the cycle also impacts the reward, encouraging long-term liquidity provision.
* **Fair Distribution**: By distributing rewards based on the total liquidity value and vToken ratio, the system ensures that rewards are fair and reasonable.

\
