# AiB BUIDL Grants and Bounties Program

## AiB BUIDL Grants and Bounties Program

The objective of this program is to provide financial support to teams and individuals who are actively contributing to the development of the proposed [AtomOne Chain](https://github.com/atomone-hub/genesis) and related software. Grants under this program range between $3,000 - $8,000 per month depending on the application, with a streamlined submission and evaluation process that ensure quick decisions. The AiB BUIDL Grants and Bounties program is funded by All in Bits with the AiB core engineering team members serving as the reviewers of all grants within the program.

This program might be a good fit if **any** of the following apply to you:

- You are an independent blockchain software developer, or a Go Developer or you are actively making commits on AtomOne Github or the Gaia fork, or are interested in AtomOne

This program’s mission is to encourage the members of the AiB contributor community to become active participants in the building and growth of the proposed AtomOne ecosystem.

- Deliverables will be specific to dedicated focus areas.
- The builder needs to cohesively explain their proposed solutions and commit to report publicly on the outcomes.
- All applications must start with a well written draft specification. It does not need to be complete, but it must be simple yet demonstrate competency and understanding of the problem.

Please note our [Terms and Conditions](https://docs.google.com/document/d/1WCZSLTYcaOHpLs-nxBD5SN1uLTuqhRPb7a9O7y-08mQ/edit) for the grant prior to application.

---

## Current Bounty Areas

### PHOTON Community Bounty

**Dates**: March 12, 2025 - TBD

**Rewards**: $200 - $10,000 USD per submission

We invite the AtomOne engineering community to analyze the security of the upcoming PHOTON module. Full details of the program are available [here](PHOTON-Community-Bounty.md).

## Areas of focus for grants:

Here are the list of focus areas the grantee can choose to contribute to, but other contributions not mentioned here may be worked on as well:

### Tendermint/Tendermint2 IBC compatibility

- **Context**: The primary goal is to port the IBC module to Tendermint2 and to demonstrate compatibility between Tendermint1 and Tendermint2 chains.
- **Resources**:
  - [https://github.com/cosmos/ibc-go](https://github.com/cosmos/ibc-go) (cosmos-sdk IBC)
  - [https://github.com/gnolang/gno/tree/master/tm2](https://github.com/gnolang/gno/tree/master/tm2) (Tendermint2)
- **Expected Deliverables(one of)**:
  - Working proof of concept of Tendermint <> Tendermint2 IBC bridge
  - Survey of changes to Tendermint2 that affect IBC
  - IBC and relayer related tooling
  - Specification documents

### AtomOne Validator Selection and ICS Crypto-Economics

**Context**: AtomOne will change the validator delegation algorithm to make validators more equal in voting power. This will increase the nakamoto coefficient of the AtomOne hub, and also make the current version of ICS (partial set security PSS) more reasonable in security. For now, assume that the initial ICS (inter-chain security) that AtomOne will support is a modified version of PSS. After, we will consider simple replicated security where all validators need to validate. Also keep in mind, we will change hub governance so that proposals don’t take delegation into account, to reduce the power of validators relative to the stakers, who can vote themselves.

The crypto-economic challenge that arises is that there needs to be a way to dis-incentivize the delegation of validators once it has already acquired the delegation needed for it to be a hub validator. It may be sufficient to distribute the hub rewards going to validators equally among the validators, such that delegators that delegate to a validator with already high delegation would see less rewards than delegating to lesser delegated validators, but this isn’t great for the early delegators, nor fair for self-delegation. Also, this doesn’t guarantee that “tail validators” have much at stake, so there probably needs to be a minimum staking requirement. When a validator gets slashed, probably all delegators should get slashed equally pro-rata, regardless of excess delegation.

It might make sense to consider a limited range of validator inequality for hub security; a validator with the most delegation might receive at most twice as much hub voting power on the hub as a validator with the least delegation, and also twice as much total hub rewards. This would allow some flexibility in delegation choice. But this is not strictly required.

With PSS, there is the issue that a validator that doesn’t have much stake behind it may end up validating for too many ICS consumer chains, thereby diluting the effectiveness of proof of stake security. In the long run we should consider the stake behind validators to be potential capital that can be used to reimburse victims of theft from validator malice. So PSS should probably be modified to limit how many consumer shards a validator may opt to validate for.

PSS earned rewards should primarily be distributed among the validators participating in the consumer chain (and these rewards are conceptually separate from hub rewards), but some portion should be redistributed to the AtomOne hub as hub rewards, so as to incentivize more equal validators. In the long run, we want AtomOne validators to be operating more or less equally secure data-centers with similar capacity.

We may remove the per-validator custom commission rate and rather apply a global effective commission rate. The commission rate is not the best means of control, and it can change too quickly after delegation resulting in a type of rug. Instead of per-validator commission rates, the overall validator selection and reward algorithm should incentivize proper distribution of delegation among the validators.

In the end, what we want is a validator selection algorithm and hub/PSS/ICS reward algorithm that gives flexibility to validators for more permissionless validation of consumer shards, while also subsidizing the growth of tail validators, to ensure the sustainable growth of more or less equal capacity validators in the long run. The algorithm must also be practical in terms of computation.

**Expected Deliverables (one of)**

- An english written specification proposal
- Crypto-economic justifications for above specification.

### AtomOne Interchain Security (ICS) Containerization and Orchestration

**Context:** AtomeOne’s ICS will initially be a fork of the current ICS (Inter-chain security) implementation in Cosmos (Partial Set Security, PSS), permissionless yet more sustainable for validators and secure for consumers than the current version. Afterwards we will also consider simple replicated security where all validators must validate; this will be used for necessary core-shards, while the permissionless system is better suited for consumer chains.

For both cases, we want the deployment of consumer shards (and later, core shards) to be as simple as possible, and the best way to achieve this is through something like linux container images. The container image would speak ABCI, and be paired with a standard consensus engine managed by AtomOne. That is, the consumer shard should not handle consensus, or P2P networking; all it does is receive transactions from ABCI and compute state changes for the consumer chain application. If the consumer provided an application image that also included a custom consensus engine, it would be impossible for AtomOne to hold validators to account.

We need several things to make this all work, but first we want to choose a specific containerization technology. The technology chosen should be minimal and auditable; this excludes technologies like Docker, but it may use the technologies that Docker uses under the hood. Whatever we end up using, we want to commit to a standard that can be maintained in the long run.

We also need improvements to the ABCI specification and the consensus engine to handle additional message types and logic that is necessary for our model of ICS. For example, validator set changes should not originate from the application, but rather they should originate from the hub, and all PSS consumer shards and the chosen validators should be represented on the hub. We can assume that all PSS consumer shards’ consensus engine instance (e.g. Tendermint or Tendermint2) has privileged RPC access to read the state of the hub.

We also need corresponding custom AtomOne orchestration software that validators can use to automate the scaling of validation services to additional consumer shards. Strictly speaking AtomOne PSS may not require the usage of this orchestration software, and validators may choose to manually onboard new consumer chains, but in the long run everything will become automated and standardized.

**Resources**

- [https://github.com/atomone-hub/genesis/blob/main/README.md#2-ibcics-hub-and-minimalism](https://github.com/atomone-hub/genesis/blob/main/README.md#2-ibcics-hub-and-minimalism)
- [https://github.com/atomone-hub/genesis/labels/ICS](https://github.com/atomone-hub/genesis/labels/ICS)
- [https://github.com/cosmos/interchain-security/blob/main/docs/docs/adrs/adr-015-partial-set-security.md](https://github.com/cosmos/interchain-security/blob/main/docs/docs/adrs/adr-015-partial-set-security.md)

**Expected Deliverables (one of)**

- Proposed design specifications for the AtomOne ICS PSS design.
- Proposed design specifications for the AtomOne ICS container technology.
- Proposed design specifications for changes to Tendermint2 on the consumer chain side, such as corresponding ABCI changes.
- Proposed design specifications for orchestration software.
- Proof of concept of a running infrastructure, whether using containers or not.
- Fork of [https://github.com/cosmos/interchain-security](https://github.com/cosmos/interchain-security)

### Tendermint2

**Context:** Tendermint2 is a fork of TendermintCore designed with principles that emphasize simplicity of design, minimal code footprint, and minimal dependencies. All dependencies are audited and included in the repository, and components are made modular wherever reasonable. The goal is to achieve completeness within a reasonable timeframe, reducing vulnerabilities and ensuring the software is finished and robust.

**Resources**

- [https://github.com/gnolang/gno/tree/master/tm2](https://github.com/gnolang/gno/tree/master/tm2)
- [https://github.com/cometbft/cometbft/blob/main/UPGRADING.md#upgrading-from-tendermint-core](https://github.com/cometbft/cometbft/blob/main/UPGRADING.md#upgrading-from-tendermint-core)

**Expected Deliverables(one of)**

- PRs and improvements to [https://github.com/gnolang/gno/tree/master/tm2](https://github.com/gnolang/gno/tree/master/tm2)
- Survey of changes to CometBFT that should be downstreamed to Tendermint2.
- Upstream PRs to CometBFT.
- Bug fixes and improvements.

---

### Requirements

We're flexible in what you choose to focus on, but we do have some clear rules for the grants we fund:

- Work funded by AiB BUIDL Grants and Bounties Program must align with AtomOne's proposed mission and scope.
- Any output must be open source, transparent or otherwise freely available

### Eligibility

We are happy to hear from all contributors who are working within our scope:

- Individuals, teams or organizations.
- Builders who meet the minimum age required by local laws in their jurisdiction in accordance with our Terms and Conditions.
- If you are selected as one of the Grant’s recipients, we are required to perform KYC before transferring funds to you, and will need to know your real identity to complete that process. However, we are happy to keep that information confidential if requested to do so, and will use a pseudonym or omit your full name entirely at your option in any communications that will be visible to anyone else.

### How do AiB BUIDL Grants and Bounties get funded?

The AiB BUIDL Grants and Bounties program is funded by All in Bits. All grants will be paid in fiat currency. Please note that individual grantees or team leads from all grant applicants will be required to complete a KYC process prior to payment of their grant. The average processing time for an application to be processed is 2 weeks. We will send you an email via grants@allinbits.com requesting that you provide your documents as necessary to complete the KYC.

We want the funding and grant process to be as transparent and easy as possible, which is why we will conduct all of the interaction, feedback loops, and updates on GitHub.

The AiB BUIDL Grants and Bounties program has a hard limit of **$3,000** to **$8,000** per month, but if you anticipate needing more to get to the finish line, you have options.

AiB BUIDL Grants and Bounties program end is individual for each focus area and will be communicated to applicants upon grant contracts. The outcome of the grant will be reviewed and scored prior to the Program conclusion.
The minimum duration of the grant program is 2 months. The grant agreement is subject to extension based on the outcome of the grantee’s contribution.

---

## Application for AiB BUIDL Grants and Bounties Program:

- Name
- Project name (if applicable)
- Email of main point of contact
- Individual/team members (GitHub handles, Twitter, websites….)
- Your chosen Area of focus for the grant
- A short description of what you are proposing (applies to all submissions)
- Why are you best suited/what is your background and previous projects that you have worked on (or team’s if applicable) (applies to all submissions)
- Objectives, milestones, deliverables and overall time frame of your proposal
- Disclosure of any conflicts of interest

### Tips for submitting your application

The information you submit here is what we will use to make a final decision about your grant application so be sure to share your grand vision in your proposal - but you also need to tell us, concretely, how you plan to achieve your goals.

Following the submission and informational session, the grant team will review the submission and follow up with more questions, status updates, and general due diligence to move to the final round. The goal is to collect as much information and feedback for the review committee to make the process as streamlined, transparent and thorough as possible for everyone.

### How to apply for a grant?

To start the process, you’ll need to:

- Fork the allinbits/grants repository
- Create a new file in AiB BUIDL Grants and Bounties program folder with your project’s name
- Outline your proposal in that file as outlined in the grant application template
- Create a Pull Request
- Email us at grants@allinbits.com and we’ll get in touch
- Fulfill the KYC requirements, if/when your submission gets approved.


### What to expect after submitting the grant application?

- All grantees will be onboarded to one or more communication channels to ensure direct interaction with the core team, send status and project updates, and facilitate ongoing follow-up.
- The grantee is regularly expected to attend the public community townhall meetings to discuss the current work that you are doing and the progress you have completed
- We will host a sourcing call with approved applicants to review how to provide live feedback and address questions from the community
- If your grant application is under consideration it will be tagged 'under evaluation' and, if it is moved to pre-approved, you will receive an email outlining the next steps in the approval process.
- All grants are subject to successful completion of the KYC requirements

## Additional Resources:

- [https://github.com/atomone-hub/genesis](https://github.com/atomone-hub/genesis)
- [https://github.com/atomone-hub/genesis/blob/main/CONSTITUTION.md](https://github.com/atomone-hub/genesis/blob/main/CONSTITUTION.md)
- [https://github.com/gnolang/gno](https://github.com/gnolang/gno)
- [gno.land](https://gno.land)
