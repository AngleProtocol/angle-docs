---
description: The Guardian to take rapid decisions in a crisis
---

# 💂 Angle Guardian

## 🔎 TL;DR

- As in any protocol, it may be necessary to rapidly pause some functionalities, to change some parameters or references in the protocol in order to react rapidly to unforeseen events.
- Angle Core Team and involved stakeholders control an address in a Gnosis multi-sig that has the rights to perform such changes.

## 💡 Need for a Guardian

The Angle Guardian is an address with specific roles and privileges in the Angle Protocol. All the privileges of the guardian are also available to the governor addresses of the Angle Protocol.

This guardian address is currently held by Angle Core Team in a [a 2/4 Gnosis Multisig](https://etherscan.io/address/0x0C2553e4B9dFA9f83b1A6D3EAB96c4bAaB42d430) controlled by the same Core Team members of the protocol as those in the Governor multisig plus [teddav](https://twitter.com/0xteddav).

If a guardian address with specific rights is needed, it is because there could be issues in the protocol which are time sensitive. In case there is a flaw in one of the contracts where an attacker can systematically make a profit, we should be able to pause the necessary parts of the contract without having to wait for the end of a governance vote for its execution.

{% hint style="info" %}
The Governor can revoke the Guardian ability at any time.
{% endhint %}

## 🔘 Responsibilities

In clear terms, the guardian can:

- Pause and unpause some contracts functionalities
- Update rapidly some parameters like users minting and burning fees, or the debt ratio for a lending strategy

{% hint style="info" %}
Everything has been designed to limit a guardian's ability to impact the protocol in a way that is harmful to the system. For instance, a guardian cannot modify references to an oracle contract and hence manipulate prices at its advantage.
{% endhint %}

## Status

This role is currently held by [a 2/4 Gnosis Multisig](https://etherscan.io/address/0x0C2553e4B9dFA9f83b1A6D3EAB96c4bAaB42d430) controlled by Core Team members of the protocol (the same as in the Governor multisig plus [teddav](https://twitter.com/0xteddav)).
