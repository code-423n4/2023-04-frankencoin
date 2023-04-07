# ✨ So you want to sponsor a contest

This `README.md` contains a set of checklists for our contest collaboration.

Your contest will use two repos: 
- **a _contest_ repo** (this one), which is used for scoping your contest and for providing information to contestants (wardens)
- **a _findings_ repo**, where issues are submitted (shared with you after the contest) 

Ultimately, when we launch the contest, this contest repo will be made public and will contain the smart contracts to be reviewed and all the information needed for contest participants. The findings repo will be made public after the contest report is published and your team has mitigated the identified issues.

Some of the checklists in this doc are for **C4 (🐺)** and some of them are for **you as the contest sponsor (⭐️)**.

---
# Repo setup

## ⭐️ Sponsor: Add code to this repo *Input Luzius🔴

- [ ] Create a PR to this repo with the below changes:
- [ ] Provide a self-contained repository with working commands that will build (at least) all in-scope contracts, and commands that will run tests producing gas reports for the relevant contracts.
- [ ] Make sure your code is thoroughly commented using the [NatSpec format](https://docs.soliditylang.org/en/v0.5.10/natspec-format.html#natspec-format).
- [ ] Please have final versions of contracts and documentation added/updated in this repo **no less than 24 hours prior to contest start time.**
- [ ] Be prepared for a 🚨code freeze🚨 for the duration of the contest — important because it establishes a level playing field. We want to ensure everyone's looking at the same code, no matter when they look during the contest. (Note: this includes your own repo, since a PR can leak alpha to our wardens!)


---

## ⭐️ Sponsor: Edit this README

Under "SPONSORS ADD INFO HERE" heading below, include the following:

- [ ] Modify the bottom of this `README.md` file to describe how your code is supposed to work with links to any relevent documentation and any other criteria/details that the C4 Wardens should keep in mind when reviewing. ([Here's a well-constructed example.](https://github.com/code-423n4/2022-08-foundation#readme))
  - [ ] When linking, please provide all links as full absolute links versus relative links
  - [ ] All information should be provided in markdown format (HTML does not render on Code4rena.com)
- [ ] Under the "Scope" heading, provide the name of each contract and:
  - [ ] source lines of code (excluding blank lines and comments) in each
  - [ ] external contracts called in each
  - [ ] libraries used in each
- [ ] Describe any novel or unique curve logic or mathematical models implemented in the contracts
- [ ] Does the token conform to the ERC-20 standard? In what specific ways does it differ?
- [ ] Describe anything else that adds any special logic that makes your approach unique
- [ ] Identify any areas of specific concern in reviewing the code
- [ ] Optional / nice to have: pre-record a high-level overview of your protocol (not just specific smart contract functions). This saves wardens a lot of time wading through documentation.
- [ ] See also: [this checklist in Notion](https://code4rena.notion.site/Key-info-for-Code4rena-sponsors-f60764c4c4574bbf8e7a6dbd72cc49b4#0cafa01e6201462e9f78677a39e09746)
- [ ] Delete this checklist and all text above the line below when you're ready.

---

# Frankencoin contest details
- Total Prize Pool: $60,500 USDC 
  - HM awards: $42,500 USDC 
  - QA report awards: $5,000 USDC 
  - Gas report awards: $2,500 USDC 
  - Judge awards: $6,000 USDC 
  - Lookout awards: $4,000 USDC 
  - Scout awards: $500 USDC
- Join [C4 Discord](https://discord.gg/code4rena) to register
- Submit findings [using the C4 form](https://code4rena.com/contests/2023-04-frankencoin-contest/submit)
- [Read our guidelines for more details](https://docs.code4rena.com/roles/wardens)
- Starts April 12, 2023 20:00 UTC 
- Ends April 17, 2023 20:00 UTC 

## Hello Wardens 👋

Yes! You're here! Awesome. We are super excited for your journey on unpacking and dissecting our code. We will do our best to be available around the clock for all your questions, small, big, silly or severe.

You'll find the most important links & communication channels at the bottom 👇 

We wish you luck on your audit.

Happy hunting 🕵

_Frankencoin team_

## Automated Findings / Publicly Known Issues *Input Luzius🔴

Automated findings output for the contest can be found [here](add link to report) within an hour of contest opening.

*Note for C4 wardens: Anything included in the automated findings output is considered a publicly known issue and is ineligible for awards.*

[ ⭐️ SPONSORS ADD INFO HERE ]

# Introduction to Frankencoin *Review Luzius🟠

## Motivation

_Democratization of Money Creation_: Today, money is created by central banks and multiplied by commercial banks, that indirectly determine the resource allocation in the economy. This leads to overinvestment in government bonds and real estate, and underinvestment in innovation and growth.

Our vision is that anyone with eligible collateral can create their own money, thereby decentralizing the resource allocation process. This unlocks growth and prosperity.

## What is Frankencoin?

The Frankencoin (ZCHF), an oracle-free, collateralized Swiss Franc stablecoin that is intended to track the value of the Swiss Franc. Our mission is to create a stablecoin that addresses the current issues faced by existing stablecoins. These issues include trusting centralized third parties, dependence on centralized oracles, and limitations in the types of collateral available to mint the stablecoin.

It's governance is decentralized, with anyone being able to propose new minting mechanisms and anyone who contributed more than 3% to the stability reserve being able to veto new minting mechanisms. 

So far, the Frankencoin has two approved minting mechanism. Both are accessible through this frontend. One is a simple swap contract to convert XCHF (CryptoFranc, fiat-collateralized stablecoin) into ZCHF and back. 

The other is a novel collateralized minting mechanism based on auctions. Unlike the minting mechanisms of other collateralized stablecoins, Frankencoin's auction-based mechanism does not depend on external oracles. It is very flexible with regards to the used collateral. In principle, it supports any collateral with sufficient availability on the market. However, its liquidation mechanism is slower than that of other collaterlized stablecoins, making it less suitable for highly volatile types of collateral. The name is inspired by the system's self-governing nature.

# Overview *Review Luzius🟠

*Please provide some context about the code being audited, and identify any areas of specific concern in reviewing the code. (This is a good place to link to your docs, if you have them.)*

The focus of this audit are the smart contracts that comprise key parts of the Frankecoin app, namely the minting of Frakencoin tokens (ZCHF), the purchase of reserve pool shares, and the stablecoin conversion between XCHF and ZCHF. It is vital that there are no possibilities to mint infinite Frankencoins and that no one's deposited collateral can be stolen.

# Scope / Contracts *Input Luzius🔴

*List all files in scope in the table below (along with hyperlinks) -- and feel free to add notes here to emphasize areas of focus.*

*For line of code counts, we recommend using [cloc](https://github.com/AlDanial/cloc).* 

| Contract | SLOC | Purpose | Libraries used |  
| ----------- | ----------- | ----------- | ----------- |
| [contracts/folder/sample.sol](contracts/folder/sample.sol) | 123 | This contract does XYZ | [`@openzeppelin/*`](https://openzeppelin.com/contracts/) |

# Points of Interest *Input Luzius🔴

*All funds are expected to be secure through the all contracts.



## Out of scope *Input Luzius🔴

*List any files/contracts that are out of scope for this audit.* 

# Additional Context *Input Luzius🔴

*Describe any novel or unique curve logic or mathematical models implemented in the contracts*

*Sponsor, please confirm/edit the information below.* *Input Luzius🔴

## Scoping Details 
```
- If you have a public code repo, please share it here:  
- How many contracts are in scope?:   16
- Total SLoC for these contracts?:  900
- How many external imports are there?: 0  
- How many separate interfaces and struct definitions are there for the contracts within scope?:  6
- Does most of your code generally use composition or inheritance?:   Composition
- How many external calls?:   0
- What is the overall line coverage percentage provided by your tests?:  70
- Is there a need to understand a separate part of the codebase / get context in order to audit this part of the protocol?:  true 
- Please describe required context:   There is a paper describing the economics of the system.
- Does it use an oracle?:  No
- Does the token conform to the ERC20 standard?: Yes 
- Are there any novel or unique curve logic or mathematical models?: There are two novel logics in the system. The first one is an auction mechanism to liquidate collateral. The second one is a built-in bonding curve when creating or redeeming equity tokens.
- Does it use a timelock function?: Yes *Review Luzius🟠
- Is it an NFT?: No
- Does it have an AMM?: No
- Is it a fork of a popular project?: No  
- Does it use rollups?: No
- Is it multi-chain?: No
- Does it use a side-chain?: No
- Describe any specific areas you would like addressed. E.g. Please try to break XYZ.": It is vital that there are no possibilities to mint infinite Frankencoins and that no one's deposited collateral can be stolen.
- Do you have a preferred timezone for communication?: CET
```

# Tests *Input Luzius🔴

*Provide every step required to build the project from a fresh git clone, as well as steps to run the tests with a gas report.* 

*Note: Many wardens run Slither as a first pass for testing.  Please document any known errors with no workaround.* 


# Links
[Frankencoin App](https://frankencoin.com/)

[Documentation](https://docs.frankencoin.com/)

[Blog](https://frankencoin.substack.com/)

[Forum](https://github.com/Frankencoin-ZCHF/FrankenCoin/discussions)

[Telegram](https://t.me/frankencoinzchf)


