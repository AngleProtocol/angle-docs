---
description: The Guardian to take rapid decisions in a crisis
---

# 💂 Angle Guardian

## 🔎 TL;DR

* As in any protocol, it may be necessary to rapidly pause some functionalities, to change some parameters or references in the protocol.
* Angle Core Team and involved stakeholders control an address in a Gnosis multi-sig that has the rights to perform such changes.

## 💡 Need for a Guardian

The Angle Guardian is an address being granted the Guardian role in the contracts at deployment. The governor address of Angle Protocol, controlled by the DAO also has this role. Each new governor address will also be given this role.

This guardian address is held by Angle Core Team in a multi-sig. The idea is that this address is able to renounce the role or to transition to a community held multi-sig several months after launch.

If a guardian address is needed, it is because there could be issues in the protocol which are time sensitive. In case there is a flaw in one of the contracts where an attacker can systematically make a profit, we should be able to pause the necessary parts of the contract without having to wait for the minimum window between a proposal coming from the DAO and its execution.

The guardian can pause functionalities. It also has the ability to change the fee parameters for some contracts.

{% hint style="info" %}
The Governor can revoke the Guardian ability at any time.
{% endhint %}

## 🔘 Responsibilities

In clear terms, the guardian can:

* Pause and unpause some contracts functionalities
* Update rapidly some parameters like users minting and burning fees, or the debt ratio for a lending strategy

{% hint style="info" %}
Everything has been designed to limit a guardian's ability to impact the protocol in a way that is harmful to the system. For instance, a guardian cannot modify references to an oracle contract and hence manipulate prices at its advantage.
{% endhint %}
