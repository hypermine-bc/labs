---
title: "Inflation in the Cosmos Ecosystem"
date: 2022-04-11T12:30:05+05:30
draft: false
categories: ["cosmos", "blockchain", "tokenomics"]
tags: ["blockchain", "inflation", "cosmos",]
banner: "/images/inflation-cosmos/cover.png"
authors:
  - arnab
---

We are quite familiar with what inflation is in real life. When the supply falls short of demand, the cost of goods and services increase, thus inflation. You can read more about inflation [here](https://en.wikipedia.org/wiki/Inflation). But what does it really mean in the world of Cosmos?

Unlike real world, Inflation in Cosmos refers to the increase in minted tokens for each block, which are used to incentivize the stakeholders. Cosmos SDK allows us to set the parameters for initial inflation rate and the paramters related to it. One of the key factors that influence inflation rate is **Goal Bonded Ratio**

**Goal Bonded Ratio** is the target staking participation ratio that the blockchain aims to achieve, and it encourages staking in the blockchain. The higher Goal Bonded Ratio is, the inflation increases at a faster rate, and vice versa<sup>[1]</sup>. The rate change of inflation is defined by: `[ 1 - {(Current Staking Ratio)/(Goal Bonded Ratio)} ] * (Current Inflation Rate Change)`

There are three scenarios for inflation rate based on Staking Ratio:

- If the current staking participation ratio is less than Goal Bonded Ratio, the inflation increases.
- If the current staking participation ratio is equal to Goal Bonded Ratio, the inflation stays constant.
- If the current staking participation ratio is greater than Goal Bonded Ratio, the inflation decreases.

We can also approximate the reward rate that stakers will earn with this formula<sup>[2]</sup>: `(Inflation Rate)/(Current Staking Ratio)`

## Cosmos `mint` module

The `mint` module in Cosmos SDK allows to query the parameters which are related to minting in Cosmos SDK. These are:

1. **Inflation Rate Change**: It determines the rate at which inflation will increase or decrease.
2. **Maximum and Minimum Inflation Rate**: Boundary limits for inflation rate
3. **Goal Bonded**: Target Staking Ratio
4. **Blocks Per Year**: Assumed number of blocks to be minted per year
5. **Annual Provisions**: It is the product of total supply and inflation rate. We can estimate the minted token of each block with this formula: `(Annual Provisions)/(Blocks Per Year)`

CLI Commands:

- Inflation Rate -> ```hid-noded query mint inflation```
- Annual Provisions -> ```hid-noded query mint annual-provisions```
- Parameters related to minting -> ```hid-noded query mint params```

To observe the impact of said parameters on inflation, following experiments were performed:

**1. Inflation Rate v/s Minted Token Quantity**

|  Inflation Rate | Minted Token Quantity |
| ------------------------------ | ------------------------------ |
| 0.13 | 2059 |
| 0.15 | 2376 |
| 0.150027712013391456 | 2377 |
| 0.150095962009955910 | 2378 |
| 0.150162639431067902 | 2379 |

As the value of inflation rate increases, the number of tokens being minted also increases as well.

**2. Blocks per year v/s Minted Token Quantity**

| Blocks per year | Minted Token Quantity |
| ------------- | ---------- |
| 6311520 | 2377 |
| 6411520 | 2339 |
| 6911520 | 2170 |
| 8111520 | 1849 |

As the number of Blocks per year were increased, the number of tokens being minted decreased gradually.

Following are the parameter figures taken from Cosmos Hub and PersistenceOne:

**Cosmos Hub**

| Parameters | Value |
| ------------- | ---------- |
| Initial Inflation Rate | 0.13 |
| Minimum Inflation Rate | 0.07 |
| Maximum Inflation Rate | 0.20 |
| Inflation Rate Change | 0.13 |
| Goal Bonded | 0.67 |
| Blocks Per Year | 4360000 |

**PersistenceOne**

| Parameters | Value |
| ------------- | ---------- |
| Initial Inflation Rate | 0.35 |
| Minimum Inflation Rate | 0.07 |
| Maximum Inflation Rate | 0.20 |
| Inflation Rate Change | 0.13 |
| Goal Bonded | 0.67 |
| Blocks Per Year | 6311520 |

## References

1. https://github.com/gavinly/CosmosParametersWiki/blob/master/Mint.md
2. https://www.figment.io/resources/cosmos-inflation-staking-rewards-how-are-they-related
3. https://docs.cosmos.network/master/modules/mint/