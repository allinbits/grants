# Photon Community Bounty

In preparation for the deployment of the Photon module to the AtomOne blockchain, All in Bits (AiB) is sponsoring a security bounty program for the AtomOne community. As we value the expertise of our developer community, we invite them to review the Photon module and report their findings. In conjunction with ongoing third-party security audits, we believe security bounty programs like this will provide the most secure experience to AtomOne users and integrators.

## What is PHOTON?

The PHOTON token is the sole fee token of AtomOne. The only way to get PHOTONs is to burn ATONEs, with a one-way burn that is not reversible at the protocol level. This functionality is enshrined in Article 3 Section 5 of the [AtomOne Constitution](https://github.com/atomone-hub/genesis/blob/main/CONSTITUTION.md#section-5-the-photon-token). You can read more about the design in this [Architecture Decision Record](https://github.com/atomone-hub/atomone/blob/main/docs/architecture/adr-002-photon-token.md).

## What are the Rewards?

Rewards will be given according to our AtomOne bug bounty policy. For bugs unrelated to PHOTON, you can submit through the [AtomOne bug bounty program](https://hackenproof.com/programs/atomone) on the  HackenProof platform. 

| Severity |  Reward (USDC)   |
| -------- | ---------------- |
| Critical | $2,000 - $10,000 |
| High     | $1,000 - $2,000  |
| Medium   | $400 - $1,000    |
| Low      | $200 - $400      |

Rewards vary based on severity level, and contain a range based on where within that critical level the risk is assessed. Broadly speaking, some example severities could include:

* Critical: An issue resulting in the loss of funds, such as exfiltration of ATONE private keys. 
* High: An issue resulting in the subversion of the AtomOne voting process. 

Please note that all submitters will need to undergo an Identity Verification process in order to be eligible for rewards; this is required by law.

## What’s in Scope?

Source code for the PHOTON module can be found here: https://github.com/atomone-hub/atomone/tree/main/x/photon 

In order to be definitely eligible for a reward, your submission must include a working proof-of-concept exploit. Submissions that do not include this may be excluded from rewards at the discretion of AiB. 

## How To Submit

Send an email to **security [at] allinbits.com** with the subject containing the phrase “PHOTON Bug Bounty”. If you are disclosing a highly sensitive finding, you can first contact us with an email to exchange encrypted messaging contacts.

In order to receive a reward for an eligible bounty, you will need to go through a KYC process. Send an email to **legal [at] allinbits.com** with the subject “PHOTON Bug Bounty” to begin the process.

## The Fine Print

Severity will be determined by AiB based on vulnerability impact, likelihood or complexity of exploitation, and other factors. Researchers may use the Common Vulnerability Scoring System (CVSS) to assist in estimating severity when submitting reports. AiB retains discretion to determine the final severity of an issue.

### Reporting your vulnerability

* All bounty submissions must be accompanied by a Proof-of-Concept (PoC).
* Please ensure that your reports are comprehensive, including reproducible steps. Failure to provide detailed reports may render the issue ineligible for a reward.
* Please consider the attack scenario, exploitability, and impact of the bug.
* For vulnerabilities related to personally identifiable information (PII), please specify the type of PII exposed and appropriately redact PII data in your submissions.

### Performing your research

* Hackers must not impact production systems in a negative way during testing
* Please submit only one vulnerability per report, unless chaining vulnerabilities is necessary to demonstrate impact.
* Rewards are reserved for the first reporter of an issue, and are not provided for duplicate findings. Duplication occurs when an issue has either been previously reported externally or identified internally. AiB retains the decision whether to share details of a finding’s history with hackers reporting issues.
* A single bounty will be awarded for multiple vulnerabilities stemming from one underlying issue.
* Engaging in social engineering tactics such as phishing, vishing, and smishing is strictly prohibited.
* Researchers must make a good faith effort to avoid privacy violations, destruction of data, and interruption or degradation of service. You should interact only with accounts you own.

### Out of scope vulnerabilities

The following activities are considered out of scope:

* Any activity that could lead to the disruption of service (DoS, DDoS). Issues concerning DoS may be submitted, but should not be tested in a fashion resulting in disruption of service.
* Attacks requiring MITM or physical access to a user's device.
* Issues that depend on third-party services or out of scope assets
* Issues that require unlikely user interaction

### Disclosure Guidelines

* Please refrain from discussing this program or any identified vulnerabilities, including resolved ones, outside of the program without explicit consent from AiB.
* We expect all researchers to adhere to the disclosure protocols of the bug bounty platform.

### Ownership of Submissions

**Intellectual Property Waiver**: By submitting reports, findings, or any other materials ("Submissions") to the bounty program, the submitter acknowledges and agrees to waive any and all intellectual property rights, including but not limited to copyright, patent, and trademark rights, to the contents of the Submission. The submitter hereby grants AiB a non-exclusive, perpetual, irrevocable, royalty-free, worldwide license to use, reproduce, modify, adapt, publish, translate, distribute, and display the Submission in any form or medium, whether now known or later developed, for any purpose related to the bounty program or otherwise.

**Legal Responsibility for Submissions**: The submitter represents and warrants that:

* The Submission is the submitter's original work, and the submitter has all necessary rights, permissions, and authority to submit the Submission to the bounty program.
* The Submission does not infringe upon or violate any intellectual property rights, privacy rights, publicity rights, or any other rights of any third party.
* The Submission does not contain any confidential or proprietary information belonging to any third party.
* The Submission does not contain any malicious code, viruses, or other harmful components.
* The Submission does not violate any applicable laws, regulations, or ethical standards.
* The Submission does not contain any false, misleading, or deceptive information.

**Indemnification**: The submitter agrees to indemnify, defend, and hold harmless AiB, its affiliates, directors, officers, employees, agents, and representatives from and against any and all claims, demands, damages, losses, liabilities, costs, and expenses (including reasonable attorneys' fees) arising out of or related to: Any breach or alleged breach of the bounty policy by the submitter. Any third party claims that the Submission or the use of the Submission by AiB infringes upon or violates any intellectual property rights, privacy rights, publicity rights, or any other rights of any third party. Any other act or omission of the submitter in connection with the bounty program.

**Safe Harbor**: AiB welcomes responsible testing and disclosure practices from the security research community. Any activities conducted in a manner consistent with this policy will be considered authorized conduct and AiB will not initiate legal action against those researchers. If legal action is initiated by a third party against you in connection with activities conducted under this policy, we will take steps to make it known that your actions were conducted in compliance with this policy.

### Eligibility and Coordinated Disclosure Policy

AiB appreciates the time and assistance of security researchers in securing the applications we contribute to.

This policy shall be governed by and construed in accordance with applicable laws and regulations, without giving effect to any principles of conflicts of law. Any dispute, controversy, or claim arising out of or relating to this policy or the breach, termination, enforcement, interpretation, or validity thereof, including the determination of the scope or applicability of this agreement to arbitrate, shall be resolved by binding arbitration in Los Angeles, California, or another location mutually agreed to by the parties. The arbitration shall be administered by ADR Services, Inc. (“ADR Services”) and held before a sole arbitrator. The arbitration shall be binding with no right of appeal. By participating in the bounty program, the submitter agrees to be bound by this policy. AiB reserves the right to modify or update this policy at any time without prior notice. It is the submitter's responsibility to review the policy periodically for any changes.

Rewards paid under this program are subject to certain legal requirements and limitations.

### AML/KYC Requirements

Know-Your-Customer (KYC) Verification: Submitters participating in the bug bounty program must undergo a Know-Your-Customer (KYC) identity verification process. This process can be completed either through AiB or through the third-party bounty platform where applicable. KYC verification is necessary to ensure the authenticity of submitters and their eligibility to receive bounty rewards.

**Prohibited Jurisdictions**: Individuals domiciled in prohibited jurisdictions as defined by [OFAC](https://ofac.treasury.gov/sanctions-programs-and-country-information) and [FATF](https://www.fatf-gafi.org/en/countries.html) regulations are ineligible to participate in the bug bounty program.

**Eligibility Verification**: The identity verification process will verify that submitters are legally eligible to receive bounty rewards. This includes ensuring that submitters are not, for example, legally sanctioned entities or otherwise prohibited from participating in such programs under applicable laws and regulations.

**Age Requirement**: Submitters must be of legal age to participate in the bug bounty program and receive rewards based on their local jurisdiction. Any submitter found to be underage will be disqualified from participating and receiving rewards.

**Compliance with Applicable Laws**: Submitters are responsible for ensuring compliance with all applicable laws, regulations, and legal requirements. Any violation of laws or regulations during the submission process will result in disqualification from the bug bounty program and forfeiture of any rewards.

**Accuracy of Information**: Submitters are required to provide accurate and truthful information during the identity verification process. Any falsification or misrepresentation of identity or information will result in immediate disqualification from the bug bounty program and may lead to legal action.

**Confidentiality**: All information collected during the identity verification process will be kept confidential and used only for the purpose of administering the bug bounty program. Personal information collected by AiB will be handled in accordance with AiB’s privacy policy and applicable data protection laws.

**Exclusion of Employees and Immediate Family Members**: Submitters participating in the bug bounty program must not be employees of AiB or affiliated group companies or their immediate family members. This exclusion is implemented to prevent conflicts of interest, unfair advantages, or manipulation of the bounty program. Immediate family members include spouses, domestic partners, parents, siblings, children, and any other relatives residing in the same household as AiB employees.

**Declaration of Affiliation**: Submitters are required to declare any affiliation or relationship with AiB or its employees that may present a conflict of interest. Failure to disclose such affiliations may result in disqualification from the bug bounty program and forfeiture of any rewards.

**Fairness and Integrity**: AiB is committed to maintaining the fairness and integrity of the bug bounty program. Any attempt to manipulate or exploit the program, including by employees or their immediate family members, will result in immediate disqualification and may lead to further disciplinary action.

**Reporting Violations**: Participants are encouraged to report any suspected violations of this policy, including instances of employee or family member involvement, to the bug bounty program administrators for investigation and appropriate action.

AiB reserves the right to verify the identity of submitters at any time during the bug bounty program and to take appropriate action, including disqualification and legal action, against any submitter found to be in violation of these identity verification requirements.

Your effort in keeping the AtomOne ecosystem safe is highly appreciated!
