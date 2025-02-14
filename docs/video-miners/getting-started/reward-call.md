---
title: Reward Calls
sidebar_position: 6
---

This guide provides instructions and recommendations on the ways to call reward when [activated](/video-miners/getting-started/activation) on the Livepeer network. It is assumed you have prior knowledge about [Earnings](/video-miners/core-concepts/earnings#rewards) and that your orchestrator is [activated](/video-miners/getting-started/activation).


# About Calling Reward

By default, an active orchestrator will automatically call reward in each round, submitting an Arbitrum transaction that distributes newly minted LPT rewards to itself and its delegators.

The amount of LPT rewards distributed by the reward call depends on the orchestrator's stake, i.e. its own stake and that of its delegators. It is important to note that for orchestrators with very low stake, the ETH transaction cost of calling reward may exceed the amount of LPT rewards distributed. The threshold to profitably call reward depends on several factors, including but not limited to the market price of LPT and the current inflation rate.

## Getting Started with Reward Calls

When you first initiate reward calls, it may make economic sense for you to [disable automatic reward calls](/video-miners/getting-started/reward-call#disable-automatic-reward-calls) and then [manually call reward](/video-miners/getting-started/reward-call#manually-call-reward) in each round instead. 

You then can [enable automatic reward calls](/video-miners/getting-started/reward-call#enable-automatic-reward-calls) when you are confident that the distribution of LPT relative to the ETH transaction cost makes economic sense.

## Disable automatic reward calls

Disable automatic reward calls with the `-reward=false` flag: 

**For example:** 

```bash
livepeer \
    -network arbitrum-one-mainnet \
    -reward=false
```
> **Note:** for the purposes of this example above, all other flags are omitted.

## Manually call reward

Use `livepeer_cli` to manually call reward:

1. Estimate the current ETH transaction cost for calling reward and ensure you have enough ETH in your wallet to execute the transaction.

- The gas cost for a reward call is typically 350k-450k.
   
- Get the required gas price from [ethgasstation](https://ethgasstation.info/) or [gasnow](https://www.gasnow.org/).

- The ETH transaction cost will be the gas cost multiplied by the gas price.

2. Make sure `livepeer` is running. 

3. Run `livepeer_cli`

4. Enter the number corresponding to the `Invoke "reward"` option

5. Wait for the transaction to confirm. 

You can view this in the logs of your orchestrator, which will indicate a transaction has been submitted and confirmed on-chain.

## Enable automatic reward calls

- To enable automatic reward calls omit the `-reward=false` flag (enabled by default). 


