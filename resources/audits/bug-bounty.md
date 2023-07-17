---
description: Community Engagement Incentives
cover: ../../.gitbook/assets/Angle-bug-bounty.jpg
coverY: 0
---

# 🐛 Bug Bounty

The security of the smart contracts of the Angle Protocol is a top priority. But even putting top priority status and maximum effort, there is still possibility that vulnerabilities can exist.

To help mitigate this risk, two bug bounty programs, with Immunefi and Hats.finance, have been put in place. Angle bug bounty programs are focused around the protocol's smart contracts with a primary interest in the prevention of:

- Thefts and freezing of principal of any amount
- Thefts and freezing of unclaimed yield of any amount
- Theft of governance funds
- Governance activity disruption

## Immunefi Bug Bounty Overview

All bug submissions for the Immunefi bug bounty must go through Immunefi's bug submission process.

The Angle bug bounty page on Immunefi can be viewed [here](https://immunefi.com/bounty/angleprotocol/).

When a hacker hits the "Submit bug report" button, they will be sent to [bugs.immunefi.com](https://bugs.immunefi.com) which will guide them through the process of creating a bug report.

### Rewards by threat level

Rewards of this bounty are distributed according to the impact of the vulnerability based on the [Immunefi Vulnerability Severity Classification System](https://immunefi.com/severity-updated). This is a simplified 5-level scale, with separate scales for websites/apps and smart contracts/blockchains, encompassing everything from consequence of exploitation to privilege required to likelihood of a successful exploit.

| Level    |                     |
| -------- | ------------------- |
| Critical | up to USD \$500,000 |
| High     | USD \$20,000        |
| Medium   | USD \$2,500         |

All Critical Smart Contract bug reports require a PoC and a suggestion for a fix to be eligible for a reward. All High and Medium Smart Contract bug reports require a PoC to be eligible for a reward.

Vulnerabilities marked as “Acknowledged”, “ Accepted Risk” or “Closed” in the [Chainsecurity security review](https://github.com/AngleProtocol/angle-core/blob/main/audits/Chainsecurity%20Audit%20Report.pdf) from July 2021, in the [Sigma Prime security review](https://github.com/AngleProtocol/angle-core/blob/main/audits/Chainsecurity%20Audit%20Report.pdf) from July 2021 and in the Chainsecurity security reviews from December 2021 and April 2022 are not eligible for a reward.

Payouts are handled by the Angle team directly and are denominated in USD. However, payouts are done in ANGLE or USDC, with the choice of the ratio at the discretion of the team.

Critical-level smart contract vulnerabilities that result in the loss of user funds will have rewards additionally capped at 10% of the funds potentially affected based on the vulnerability that was identified. These rewards are payable in USDC or in ANGLE at the discretion of the team as mentioned above. ANGLE rewards will have a vesting schedule lasting between 6-12 months with a minimum of 6 months for rewards up to USD 200 000, with an additional month added for every USD 50 000 tranche, rounded up. However, there is a minimum of USD 50 000 for Critical bug reports.

Payouts are handled by Angle Labs team directly and are denominated in USD. However, payouts are done in ANGLE or USDC, with the choice of the ratio at the discretion of the team.

### Assets in Scope

The smart contracts in scope for this bounty are detailed in the [Angle bug bounty page on Immunefi](https://immunefi.com/bounty/angleprotocol/). They can be found on the [Core repo of the protocol](https://github.com/AngleProtocol/angle-core). However, only those in the Assets in Scope table are considered as in-scope of the bug bounty program.

## Hats.finance Bug Bounty Overview

[Hats.finance](https://hats.finance/) is a permissionless bug bounty solution. Every DAO token holder can deposit tokens in a vault, which will be used to pay potential white hat hackers that find vulnerabilities in the contracts in scope. Users depositing governance tokens can withdraw them with a 7 days delay.

### Contracts in scope

All Angle related contracts fall into the scope of Hats.finance bug bounty. These contracts can be found in the [developers documentation](https://developers.angle.money/overview/smart-contracts), or on Hats.finance [Angle bounty section](https://app.hats.finance/vaults).

### Submitting a vulnerability

Vulnerabilities can be submitted from [this page](https://app.hats.finance/vulnerability). Severity is decided by the committee according to the descriptions listed in the [Angle bounty section](https://app.hats.finance/vaults). The bounty is a share of the tokens deposited in the vault, depending on the severity of the bug.
