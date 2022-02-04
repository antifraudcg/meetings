# February 4, 2022

## Logistics

12-1 PM EST / 9-10AM PST / 5-6PM GMT

## Agenda

* Charter Review (10 mins)
* Use Cases and Threat Models (15 mins)
* Browser Privacy Measures - Impact to Fraud Controls - Socure (20 mins)
* Initial Work Items (15 mins)

## Resources

* [Minutes](https://docs.google.com/document/d/1pfzQ4lzgWELLCDI5dddj2OgWlY5BkAvesBN4d6WyCg4/edit?usp=sharing)
* [Chair Slides](https://docs.google.com/presentation/d/1GXxim6MqE24RzJjdEx-CKNGZxkOVLkbpb8YGwx8_4IM/edit)
* [Proposal: Use Cases & Threat Models](https://github.com/antifraudcg/proposals/blob/main/use-cases/use-cases.md)
* [Browser Privacy Measures - Impact to Fraud Controls (Sam Jackson)](https://github.com/antifraudcg/meetings/blob/main/files/socure-browser-signals-and-identity-fraud.pdf)

## Minutes

### Agenda Review

Dimitris: Invite scribes. Please familiarize yourself with the W3C code of conduct, which governs this meeting. We’d like to reach consensus on the charter over the next week. We also have a draft of use cases and threat models. We’ll hear from Socure on use cases.


### Charter Review (10 mins)

Dimitris: See the [draft charter](https://raw.githack.com/antifraudcg/antifraudcg.github.io/main/charter.html). Today we’d like to discuss a [proposed change](https://github.com/antifraudcg/antifraudcg.github.io/pull/6).

StevenV: The proposal includes language about “fraud and abuse” and also has language going beyond browsers, both in response to previous discussion. We can amend the charter later regarding “fraud and abuse” once we have more concrete use cases. If people don’t have major feedback over the next week or so, we’ll move to a call for consensus to adopt the charter.

Dimitris: Seeing nobody on the queue, we’ll look for comments and the chairs will send a CfC thereafter.

Per: Was it intentional to not use “abuse”?

StevenV: See the pull request that includes “abuse” wording; please comment on the pull request.


### Use Cases and Threat Models (15 mins)

Dimitris: This is a first draft of [use cases and threat models](https://github.com/antifraudcg/proposals/blob/main/use-cases/use-cases.md). We are using an OWASP taxonomy to describe threat classes. 

Michael McNally: Non-automated threats would be outside of OWASP scope (automation detection). Should we consider malicious human actors not using automation and their identification?

Dimitris: We used the term “programatically detecting”; we should definitely include manual threat models in the taxonomy.

Sam Jackson: I am planning to add those in a next pass.

Dimitris: Any obvious missing use cases?

Per: I’d like time to review offline in detail.

Kevin: There are some things that are not covered precisely but that I think would be in scope, such as a person misrepresenting themselves to a government agency for getting someone else's social security payments. As long as we're a little flexible about what these things mean, it should be good.

StevenV: Please make pull requests or comments on the issue that was raised on this document. This document is not yet “adopted by the CG” so please send suggestions to the authors rather than edit it directly.

Ian: Please notify the group of new resources via the CG mailing list.

Dimitris: Chairs will do that.

Nick Doty: Will DDOS be part of the use cases? There’s a variety of spam/harassment bucket. It might be useful to cross reference the IETF IP address considerations document. Would you consider DDOS in scope? \
https://datatracker.ietf.org/doc/draft-ip-address-privacy-considerations/

Dimitris: I think we should list the use cases, and then decide as a group where to focus. So the group would be exhaustive by design, and then we would identify our focus.

Brian May: Let’s develop categories and people can list what they can think of under the categories, then we can prioritize / focus. I would also ask that when there are agenda items on resources, to please make those resources available in advance of the meeting so that we may prepare.

StevenV: Regarding DDOS - I think there are some classes we would like to address, but I think some topics (e.g., packet storms / DNS-level attacks / etc.) we would likely to consider out of scope.

Nathan Tacha: There is a lot of fraud and abuse where the primary damage is done in the real world, but where the problem begins in the digital space.

Per: I think generally we will find solutions that help prevent abuse in a variety of areas. I think it will be difficult and cumbersome to come to agreement on a taxonomy (and I don’t think the taxonomy matters much). I think we should be clear that (1) what we list are examples (2) only things that are explicitly deemed out of scope are out of scope.

Brian May: +1 to Per’s concerns. I suggest we spend some time crowdsourcing things that should be in scope, then put some structure around it, and then move on.

Dimitris: +1 to Per and May. The reality is that different use cases are likely to push us in different solution spaces.

Dimitris: Logistical note: we should have a single source of truth where to find resources.


### Browser Privacy Measures - Impact to Fraud Controls - Socure (20 mins)

Sam Jackson: Socure focuses on identity verification, and fraud mitigation. Financial institutions use us for account opening process; we work with government and other industries. This is my first experience in a group like this.

Sam Jackson: Fraud is not new. But COVID has led to an explosion of account openings and corresponding large scale fraud. The US Secret Service estimates lots of fraud related to COVID assistance, for example. 

Sam Jackson: Lots of fraud happens at account opening. You need to verify user identity to establish a chain of trust. At Socure, we have found that IP signals are essential. These are also widely used in other industries like financial services. Risk signals are used in a variety of contexts, but very often “account opening” is a critical event.

Sam Jackson: Sources of entropy in the browser and signals related to IP addresses are very useful when assessing identity. Old-fashioned attributes (e.g., name, email) no longer suffice on their own. They can be easily compromised or even irrelevant in a purely digital environment. Digital identity provides a ground on which we can evaluate identity obfuscation. We are gravely concerned that some new browser privacy measures will have a significant impact on user safety and financial losses. 

Sam Jackson: One problem is ambiguity concerning emerging standards. Some of the proposals are problematic for risk assessment, such as IP masking, UA string masking, and efforts to reduce fingerprinting. If these are implemented, we expect to see significant impact:



*   Lower ability to profile and stop fraud rings
*   Inability to identify IP concealment schemes. Many of these mechanisms are good but they are also used for identity theft.
*   Limited ability to identify foreign actors or criminal networks.
*   Limited signals re: bots or traffice from hosting facilities
*   Anomaly detection
*   Customer re-identification
*   Less IP geolocation data

Sam Jackson: We also anticipate that changes will have a negative impact on AI that is typical now in this space. The models need data. Changes will reduce the amount of intelligence used for fraud modeling.

Sam Jackson: If the privacy budget is implemented, it could introduce non-deterministic behavior and be a source of volatility. Key variables may be useless or, worse, a source of noise. (e.g., Privacy Budget FAQ mentions introducing noise.) 

Sam Jackson: Many privacy measures are being instituted regarding legitimate concerns regarding marketing practices and surveillance. But fraud controls are a society good and a necessary part of our global economy. There may even be regulatory requirements for digital profiling. We hope that browsers adopt standards that balance consent-driven privacy measures with @@

Sam Jackson: One idea is to carve out exemptions for companies with an exclusive focus on fraud-detection or account security. An approach would enable high-trust interactions while respecting consent and protecting against ubiquitous surveillance. When I say “exclusive focus on fraud-detection”; it’s a reality that there are companies that do both marketing and fraud-detection.  

Brain May: I’m involved in other groups where the use cases are not directly related to advertising and privacy, but are related to them. We are trying to prioritize these use cases. I recommend that if people are aware that a use case will be impacted, that they please note it in the use cases.

Michael Ficarra: Thanks for the interesting proposal in the presentation. I work for Shape Security, an antifraud service provider, which sounds like it would be a candidate company in your approach, but we do our work in 1p context. There would not be a way for a browser to distinguish our content from content provided by our customer. So I am interested in the proposal, but it would need to take into account our kind of integration.

Sam Jackson: I imagine some combination of markup plus certification process to determine who can get the data.

Nathan: To clarify: the context is “high risk” but also where “the user sees value in executing the transaction.” Another part of this is that the legitimate consumer should have a 1p relationship with the party they are executing the transaction with. E.g., consumer trusts a bank. The bank could have an entity that acts on the bank’s behalf for anti-fraud.

Sam Jackson: We use a variety of technologies (JS, reverse proxies, server, …). There are lots of approaches. Identifying where the browser interacts with specific technology may be complicated. But we could probably describe where handshakes are likely to happen. 

Sameer Tare: Great presentation. I represent the EMVCo 3DS Working Group. The new restrictions will have an impact on risk assessment in card-not-present transactions. We have presented previously on our use cases (including a proposal). I just want to add concerns that we need to be sure to deal with the impact of these changes on risk assessment mechanisms that are out there.

Nick Doty: +1 to documenting “how we got here.” I think it’s worth noting that (1) abuse of protocols and (2) constant surveillance have motivated the emerging restrictions. I am curious about the “carve-out” approach. But I had understood that that was out-of-scope given our charter. 

Sam Jackson: I had understood “carve-out” to mean “other use cases unrelated to fraud.”

StevenV: The current wording in the charter is intended generally. If we think that carve-outs are worth pursuing, please raise issues for discussion.

Rick Byers: Thanks for the presentation. I am on the Chrome team. Can you say more about how IP addresses are used? There are some signals like “what country?” I think that is preserved in some evolving products (e.g., from Apple). Can you break apart the way that IP addresses are used? Can you think about a solution where certification is of the proxy, where some information is preserved (e.g., country info or a confidence score) and other information is redacted? I’m worried about certifying large numbers of groups. Are there options for certifying more on the “privacy site” and less on the “fraud side.”

Sam Jackson: Regarding IP address usage 3 useful things:



1. There are folks who sell signals like whether an IP is associated with a hosting facility. This is a CRITICAL signal. Fraud rates are close to 85% in this case.
2. Location is a big deal. Not “precise” location but @@. The modality of a lot of fraudsters is that people scope a house and determine whether they can steal mail/packages from the house. So at least getting a geolocation that is “reasonably proximal” is very useful. The signal is less useful the further away.
3. IP address is used to evaluate traffic patterns - are they in a location where this sort of traffic would make sense? E.g., a consumer service (cable/DSL). We can look at traffic volume for an IP address and see whether it is usual, or disproportionately high. Identity theft (e.g., stolen cards) often accompanied by increased IP address usage.

Matt Finkel: In general I am interested in looking at solutions in this group that allow users to consent to identification. Today the Web platform does not allow for that. Anti-fraud mechanisms are important, but today they are all passive. In this group and others we are looking at how users can know they are being identified and have the means to prevent it.

Per: I think we all likely want privacy and a safe online world. I think we should focus on problem statements. Solutions will involve a combination of technology and (likely) policy. I also recommend that we pursue multiple solutions because we don’t know where regulators will end up. We’ll want a variety of options. Regarding user awareness and opting in: I think that that’s generally a good principle, but it’s also important to be able to deal with abuse cases. These are all good discussions.

Shivan Sahib: I share concerns about the vagueness of privacy budget proposals. I am concerned about how users provide consent. I think it can be difficult for browsers to figure out malicious behavior; not sure how we can have proposals given this difficulty.

Sam Jackson: I imagine an auditing process. It’s a complicated proposal. But I’m looking for a balance between the new proposals and the significant impact they will have otherwise.

Brian May: A colleague shared terms of service for signing up for a gym membership that included rights to all her data, from any source, in perpetuity. I think we’ll need to consider situations like this at some level.

Sam Jackson: The unfortunate reality today is that if you opt-out of an verification mechanism, you will face a lot of onboarding friction and MORE data will be gathered (e.g., photo of passport or drivers license). By trying to avoid less invasive profiling, users end up having to provide even more information.

Summary:

*   Please review charter; expect CfC in a couple of weeks
*   Please review the use cases draft
*   Please use the issues list
*   We’ll announce new resources on the group’s list.