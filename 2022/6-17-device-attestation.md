# June 17, 2022

## Logistics

12-1 PM EDT / 9-10AM PDT / 4-5PM GMT

## Resources

* [Minutes](https://docs.google.com/document/d/1z1Wui4VupqzQxcCHnwqU1M8DkfIwc1zFiTpA65-qIN0/edit?usp=sharing)

## Minutes

Michael:



*   Related Github issue: https://github.com/antifraudcg/proposals/issues/8
*   Thanks for the meeting. Exposing Trusted Computing Hardware (TCH) to the web. How TCH can be utilized with OS toprovice a root of trust. 
*   Is device attestation only available for closed platforms? Or open source platforms are supported?
*   Hardware attested uniqueness. Exposing uniqueness originating from TPM-like HW over the web might prevent automation of scale.

Philipp on the proposal



*   Deprecating third party cookies (TPC/3PC) might lead to more fingerprinting on the web.
*   Hard to separate probing used for tracking against probing for bad actor detection
*   Reduce the amount of entropy between client and server. Even a single bit (is an iPhone, is a legit device) could help.

Borbala



*   Make fingerprinting used for  device attestation redundant.
*   What a useful API would look like: answers “is this secure?” “Is this used by a human?”
*   Secure device = integrity of the system (no malware, ) is not enough
*   Malware is important since most abuse is from real devices infected.
*   An abstraction that compromises the integrity of the device and the applications in it without compromising the privacy of it.
*   It still will need to invest into knowing that there is a human behind the device: attestation that a click happened, for example.
*   Behavioral integrity is a softer form, attesting the history of the device or user behavior.

Nathan



*   Voice support for a counter functionality: not high precision -> being able to detect hyper activity by automation or by humans -> a single device that is hyperactive is not considered trusted
*   Importance of facts: different use cases might have different ideas of trust. Users might be doing non-abuse actions and also abuse ones. See if a device is rooted: need granularity.

Michael



*   Seems like a closed platform would be required for platform integrity. Open platforms cannot be trusted (can’t make accurate observations).
*   Assuming closed platform → no clear way of not exposing sensitive information. E.g. a platform signed with a manufacturer’s key and compromised
*   Manufacturer to track the compromised platforms (OS versions meant here?). Provide the last patched version of the OS? This information might be used in fingerprinting however, crucial to the health of the device as well.

Brian



*   Seems like the intent is to supply low discrete entropy to contexts where there is no trust: a user agent and the device have trust, and they can attest to each other which (a high entropy relationship) can be used to transfer that trust to a third party attester (via a low entropy signal) without given more information?
*   Is that the idea?

Philipp



*   This is similar to how current models work. Manufacturer of the device gets high level information about the device. Does not attest to what the user is doing on the device. E.g. App Attest and Play Integrity API
*   In practice -> device manufacturers make the rules. Platform providers want to prevent x-app tracking.
*   Open source software and how we prevent: supporting howbrew software
*   FIDO alliance example for standardizing attestation, independent of who provides it

Nick



*   +1 for high entropy comms and blind them to be used in other contexts. This model is nice, does not prevent a lot of user data to third party contexts, it is not privacy perfect
*   Don’t agree with the assumption of not being able to use open source software
*   Just responding to earlier comments: in the web context, it should be considered extensions and user configuration which allows for innovation -> from an user perspective.

Michael



*   +1 for Philipp clarifying open source vs closed platforms. Fedora, as distributed by the Fedora project, is not problematic. Software compiled at home is problematic, there are no checks, nobody knows what is built, only the person who built it.
*   Mitigations for … : have a trust 3P in the middle (e.g. the manufacturer); **or** have a trusted anti-fraud provider with which the information is shared with (lists managed by user, standard lists by UA); **or** only available in user-selectable browser context (e.g. banking); **or** possibly using cryptography to mix the origin with the uniqueness that allows 1p tracking, but not x-site tracking

Steven



*   On checking patch versions. Third parties just need to know whether the device is trustable (patched correctly) not the specific patch version.

Borbala



*   Non uniformity across OS: we should aim for clean principles, indications of system integrity
*   Attestation is a useful building block, but it is not perfect: acknowledge that there will be false negatives
*   We need to think what to attest and how
*   Examples of behavioral integrity: Incentivized user detection, hyperactive user detection (hard to say what it is concretely, but there may be heuristics as a web standard)
*   Attestation is about facts. Pairing with behavior would be a good combination (call it Trust Role?)

Sandro



*   Interesting to talk about open vs closed ecosystem: EU DMA -> site loading could be law, the notion that the provider is the ultimate arbitraer will not be the case for anti-competitor

Eric



*   Support for low entropy signals. Concerned about introducing new high entropy signals. Having consent forms on every site visited is not a useful solution. 

Philipp



*   Asking for more details on the site loading topic
*   Historically: browser calls into some APIs and gets information (e.g. Chrome downloaded from App Store)

Borbala



*   Side loading, open source vs closed source. 
*   Asking the OS if you’re attested would be weird. Now: we use an attester to vouch for it. Coincidence right now that the OS is the attester as well
*   Custom built OS might eventually lead to a new ecosystem that could have attesters that can vouch for it

Brian May



*   It seems like there are levels of use case: serving an add to person vs person accessing bank account are different cases
*   Small bits of information can be integrated in a high-entropy signal

Philipp



*   There are some use cases: individual vs aggregate is important for users or servers: trivial to user or severs, but in aggregate are useful
*   Importance of device attestation to avoid consolidation in other realms: we need to maintain the device integrity. Device attestation is easier to get people into 

Nick



*   Concerned about consolidation: small number of device attesters. Curious about the case
*   Attestation that is more highly accepted, users without it could be punished for it. Is it a solution then? It could get to a point in which websites are unusable -> think proactively about ways to prevent that, or diminish the severity of the punishment

Borbala



*   An attestation provider should have a deep integration into the system: OS should set strong rules on who has that insight
*   It could be a handful of parties but maybe it will be bad if there are too many

Philipp



*   Responding to preventing people from being blocked: there are situations where the user would want a fair playing field (i.e. not being sniped by a data center bot for some tickets)

Eric



*   Potential many signals that are low-entropy, privacy preserving: reduce fingerprinting: this is a starting point: users demonstrate trust to the website that they are visiting. Universal access is important

Borbala - treating less secure devices



*   SafetyNET is very similar: lets third party developers assess the security of the device. 
*   Developers using Snet are more willing to take risks: use it as a signal as part of the anti-abuse strategy
*   What are the things we worry about? Can we influence the industry on it?

Brian



*   Potential discrimination: validating the trust of a relatipship can extend to user agent and website: website says I need this info and user decides if show or not.
*   There is a lot of opportunity here: separate use cases and come up with solutions

Chris



*   Use cases: good thing to do rather than just approach
*   Device attestation is insufficient for some cases: pushback on it. Not having such a signal seems to indicate that we don’t know if it is good enough or not

Steven (next steps):



*   Come up with use cases: discuss over Slack
*   Next side meetings
*   Overview of what happen for next meeting
*   Next meeting: trusted tokens