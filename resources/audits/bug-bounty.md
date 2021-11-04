---
description: Community Engagement Incentives
---

# 🐛 Bug Bounty

## Program Overview

At Angle, we consider the security of our systems a top priority. But even putting top priority status and maximum effort, there is still possibility that vulnerabilities can exist.

We have therefore setup a bug bounty program with the help of Immunefi. The Angle Protocol bug bounty program is focused around our smart contracts with a primary interest in the prevention of:

* Thefts and freezing of principal of any amount
* Thefts and freezing of unclaimed yield of any amount
* Theft of governance funds
* Governance activity disruption

## All bug submissions must go through Immunefi's bug submission process

The Angle bug bounty page can be viewed at the link below:

{% embed url="https://immunefi.com/bounty/angleprotocol/" %}

When a hacker hits the "Submit bug report" button, they will be sent to [bugs.immunefi.com](https://bugs.immunefi.com) which will guide them through the process of creating a bug report.&#x20;

### Rewards by threat level

Rewards are distributed according to the impact of the vulnerability based on the [Immunefi Vulnerability Severity Classification System](https://immunefi.com/severity-updated). This is a simplified 5-level scale, with separate scales for websites/apps and smart contracts/blockchains, encompassing everything from consequence of exploitation to privilege required to likelihood of a successful exploit.

#### Smart Contracts and Blockchain

| Level    |                    |
| -------- | ------------------ |
| Critical | up to USD $500,000 |
| High     | USD $20,000        |
| Medium   | USD $2,500         |

All Critical Smart Contract bug reports require a PoC and a suggestion for a fix to be eligible for a reward. All High and Medium Smart Contract bug reports require a PoC to be eligible for a reward.

Vulnerabilities marked as “Acknowledged”, “ Accepted Risk” or “Closed” in the [Chainsecurity security review](https://github.com/AngleProtocol/angle-core/blob/main/audits/Chainsecurity%20Audit%20Report.pdf) and [Sigma Prime security review](https://github.com/AngleProtocol/angle-core/blob/main/audits/Chainsecurity%20Audit%20Report.pdf) are not eligible for a reward.

Payouts are handled by the Angle Protocol team directly and are denominated in USD. However, payouts are done in ANGLE or USDC, with the choice of the ratio at the discretion of the team.

Critical-level smart contract vulnerabilities that result in the loss of user funds will have rewards additionally capped at 10% of the funds potentially affected based on the vulnerability that was identified. These rewards are payable in USDC or in ANGLE at the discretion of the team as mentionned above. ANGLE rewards will have a vesting schedule lasting between 6-12 months with a minimum of 6 months for rewards up to USD 200 000, with an additional month added for every USD 50 000 tranche, rounded up. However, there is a minimum of USD 50 000 for Critical bug reports.

### Assets in Scope

The smart contracts in scope for this bounty are detailed in the [Angle bug bounty page on Immunefi](https://immunefi.com/bounty/angleprotocol/). They can be found on the [Core repo of the protocol](https://github.com/AngleProtocol/angle-core). However, only those in the Assets in Scope table are considered as in-scope of the bug bounty program.

### Impacts in Scope

Only the following impacts are accepted within this bug bounty program. All other impacts are not considered as in-scope, even if they affect something in the assets in scope table.

#### Smart Contracts and Blockchain

* Loss of user funds staked by freezing or theft
* Loss of governance funds
* Smart contracts fails to deliver promised returns
* Temporary freezing of funds for any amount of time
* Theft/Freezing of unclaimed yield
* Smart contract fails to deliver promised returns
* Vote Manipulation
* Unable to call smart contract

### Prioritized vulnerabilities

We are especially interested in receiving and rewarding vulnerabilities of the following types:

#### Smart Contracts and Blockchain

* Re-entrancy
* Logic errors
  * including user authentication errors
* Solidity/EVM details not considered
  * including integer over-/under-flow
  * including rounding errors
  * including unhandled exceptions
* Trusting trust/dependency vulnerabilities
  * including composability vulnerabilities
* Oracle failure/manipulation
* Novel governance attacks
* Economic/financial attacks
  * including flash loan attacks Congestion and scalability
  * including running out of gas
  * including block stuffing
  * including susceptibility to frontrunning
* Consensus failures
* Cryptography problems
  * Signature malleability
  * Susceptibility to replay attacks
  * Weak randomness
  * Weak encryption
* Susceptibility to block timestamp manipulation
* Missing access controls / unprotected internal or debugging interfaces

#### Out of Scope & Rules

The following vulnerabilities are excluded from the rewards for this bug bounty program:

* Attacks that the reporter has already exploited themselves, leading to damage
* Attacks requiring access to leaked keys/credentials
* Attacks requiring access to privileged addresses (governance, strategist)

#### Smart Contracts and Blockchain

* Incorrect data supplied by third party oracles
  * Not to exclude oracle manipulation/flash loan attacks
* Basic economic governance attacks (e.g. 51% attack)
* Lack of liquidity
* Best practice critiques
* Sybil attacks

The following activities are prohibited by this bug bounty program:

* Any testing with mainnet or public testnet contracts; all testing should be done on private testnets
* Any testing with pricing oracles or third party smart contracts
* Attempting phishing or other social engineering attacks against our employees and/or customers
* Any testing with third party systems and applications (e.g. browser extensions) as well as websites (e.g. SSO providers, advertising networks)
* Any denial of service attacks
* Automated testing of services that generates significant amounts of traffic
* Public disclosure of an unpatched vulnerability in an embargoed bounty
