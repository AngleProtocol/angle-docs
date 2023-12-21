---
description: The Guardian to take rapid decisions in a crisis
---

# 💂 Angle Guardian

## 🔎 TL;DR

- Like in any protocol, it may be necessary to rapidly pause some functionalities, to change some parameters or references in the protocol in order to react rapidly to unforeseen events.
- The protocol has a multisig on each of the chains on which it is deployed which has the rights to perform such changes.

## 💡 Need for a Guardian

The Guardian role is a privileged role granted to some addresses on every chain where the protocol is deployed. All the privileges of the guardian are also available to the governor addresses (e.g. the `Timelock` addresses) of the Angle Protocol.

This guardian role is currently held on every chain by:

- the [4/6 emergency multisig](./angle-dao.md#canceller-role-and-emergency-multisig) of the protocol
- a 2/3 Gnosis Multisig controlled by the same Angle Labs team members as those in the emergency multisig (the 3 co-founders of the project).

If a guardian role with specific rights is needed, it is because there could be some situations in the protocol which are time sensitive. In case there is a flaw in one of the contracts where an attacker can systematically make a profit, we should be able to pause the necessary parts of the contract without having to wait for the end of a governance vote for its execution.

Note however that governance can revoke the guardian ability to any address at any time.

{% hint style="info" %}
Address of the 2/3 guardian multisig across different chains can be found [here](https://developers.angle.money/overview/smart-contracts).
{% endhint %}

## 🔘 Responsibilities

In clear terms, the guardian role enables to:

- Pause and unpause some contracts functionalities
- Update rapidly some parameters like users minting and burning fees, or the debt ceiling for an asset in the borrowing module
- [Some governance votes](https://snapshot.org/#/anglegovernance.eth/proposal/0xf9f6528492784d496f6edd91ee748f1d1e6bd213d86cf09e891fb93642a6c7c2) have also granted a guardian address with the ability to occasionally sponsor the acquisition of some collateral assets within the Transmuter system on a budget granted by governance

{% hint style="info" %}
Angle smart contracts have been designed to limit a guardian's ability to impact the protocol in a way that is harmful to the system. For instance, a guardian cannot modify references to an oracle contract and hence manipulate prices at its advantage.
{% endhint %}
