---
description: The Guardian to take rapid decisions in a crisis
---

# 💂 Angle Guardian

## 🔎 TL;DR

- Like in any protocol, it may be necessary to rapidly pause some functionalities, to change some parameters or references in the protocol in order to react rapidly to unforeseen events.
- The protocol has a multisig on each of the chains on which it is deployed which has the rights to perform such changes.

## 💡 Need for a Guardian

The Angle Guardian is an address with specific roles and privileges in the Angle Protocol. All the privileges of the guardian are also available to the governor addresses of the Angle Protocol.

This guardian address is currently held in a 2/3 Gnosis Multisig in each of the chain on which the protocol is deployed. It is controlled by the same Angle Labs team members as those in the Governor/Emergency multisig (the 3 co-founders of the project).

If a guardian address with specific rights is needed, it is because there could be some situations in the protocol which are time sensitive. In case there is a flaw in one of the contracts where an attacker can systematically make a profit, we should be able to pause the necessary parts of the contract without having to wait for the end of a governance vote for its execution.

Note however that any governance address can revoke the guardian ability at any time.

{% hint style="info" %}
Address of the Guardian multisig across different chains can be found [here](https://developers.angle.money/overview/smart-contracts).
{% endhint %}

## 🔘 Responsibilities

In clear terms, the guardian can:

- Pause and unpause some contracts functionalities
- Update rapidly some parameters like users minting and burning fees, or the debt ceiling for an asset in the borrowing module
- [Some governance votes](https://snapshot.org/#/anglegovernance.eth/proposal/0xf9f6528492784d496f6edd91ee748f1d1e6bd213d86cf09e891fb93642a6c7c2) have also granted the guardian address with the ability to occasionally sponsor the acquisition of some collateral assets within the Transmuter system on a budget granted by governance

{% hint style="info" %}
Everything has been designed to limit a guardian's ability to impact the protocol in a way that is harmful to the system. For instance, a guardian cannot modify references to an oracle contract and hence manipulate prices at its advantage.
{% endhint %}
