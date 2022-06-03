---
description: Community Engagement Incentives
---

# 🐛 Bug Bounty

## Program Overview

At Angle, we consider the security of our systems a top priority. But even putting top priority status and maximum effort, there is still possibility that vulnerabilities can exist.

We have therefore setup a bug bounty program with the help of Immunefi. The Angle Protocol bug bounty program is focused around our smart contracts with a primary interest in the prevention of:

- Thefts and freezing of principal of any amount
- Thefts and freezing of unclaimed yield of any amount
- Theft of governance funds
- Governance activity disruption

## All bug submissions must go through Immunefi's bug submission process

The Angle bug bounty page can be viewed at the link below:

{% embed url="https://immunefi.com/bounty/angleprotocol/" %}

When a hacker hits the "Submit bug report" button, they will be sent to [bugs.immunefi.com](https://bugs.immunefi.com) which will guide them through the process of creating a bug report.&#x20;

### Rewards by threat level

Rewards are distributed according to the impact of the vulnerability based on the [Immunefi Vulnerability Severity Classification System](https://immunefi.com/severity-updated). This is a simplified 5-level scale, with separate scales for websites/apps and smart contracts/blockchains, encompassing everything from consequence of exploitation to privilege required to likelihood of a successful exploit.

#### Smart Contracts and Blockchain

| Level    |                     |
| -------- | ------------------- |
| Critical | up to USD \$500,000 |
| High     | USD \$20,000        |
| Medium   | USD \$2,500         |

All Critical Smart Contract bug reports require a PoC and a suggestion for a fix to be eligible for a reward. All High and Medium Smart Contract bug reports require a PoC to be eligible for a reward.

Vulnerabilities marked as “Acknowledged”, “ Accepted Risk” or “Closed” in the [Chainsecurity security review](https://github.com/AngleProtocol/angle-core/blob/main/audits/Chainsecurity%20Audit%20Report.pdf) from July 2021, in the [Sigma Prime security review](https://github.com/AngleProtocol/angle-core/blob/main/audits/Chainsecurity%20Audit%20Report.pdf) from July 2021 and in the Chainsecurity security review from December 2021 are not eligible for a reward.

Payouts are handled by the Angle Protocol team directly and are denominated in USD. However, payouts are done in ANGLE or USDC, with the choice of the ratio at the discretion of the team.

Critical-level smart contract vulnerabilities that result in the loss of user funds will have rewards additionally capped at 10% of the funds potentially affected based on the vulnerability that was identified. These rewards are payable in USDC or in ANGLE at the discretion of the team as mentionned above. ANGLE rewards will have a vesting schedule lasting between 6-12 months with a minimum of 6 months for rewards up to USD 200 000, with an additional month added for every USD 50 000 tranche, rounded up. However, there is a minimum of USD 50 000 for Critical bug reports.

Payouts are handled by our Core Team team directly and are denominated in USD. However, payouts are done in ANGLE or USDC, with the choice of the ratio at the discretion of the team.

### Assets in Scope

The smart contracts in scope for this bounty are detailed in the [Angle bug bounty page on Immunefi](https://immunefi.com/bounty/angleprotocol/). They can be found on the [Core repo of the protocol](https://github.com/AngleProtocol/angle-core). However, only those in the Assets in Scope table are considered as in-scope of the bug bounty program.
