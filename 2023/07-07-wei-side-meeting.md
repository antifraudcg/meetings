# July 7, 2023

## Logistics

12-1 PM EDT / 9-10AM PDT / 4-5PM GMT

## Agenda

* Web Environment Integrity/privacypass Side Meeting

## Resources

* [Minutes](https://docs.google.com/document/d/1HOPyVagFTDPJFWaZcX4u93Yu-LSigLFd3bPP8Nix7cM/edit?usp=sharing)

## Minutes

Steven: This is a breakout meeting to discuss ‘Web Environment Integrity’ as it relates to Privacy Pass.

Tommy: Sounds fine to extend Privacy Pass to JS API. That was out of scope for the IETF working group, but makes sense as an extension.

Mariana: Defining the privacy property that we will be preserving here. Differences between single vs multi use credentials, will result in different privacy properties/definitions. Can the tokens be modified in a way such the token itself cannot be reused in a separate question.

Philipp: I want to separate the reuse from private vs public. For the signing component, is that itself concerning?

Mariana: I don’t think that’s worrisome on it’s own, can think of a different way to think of one-time use tokens.

Tommy: Clarifying question: If the device has the private key, is the device able to respond to a challenge locally because it has had some interaction with the issuer path already?

Philipp: That’s right. 

Tommy: It sounds like motivation for that would be more latency, rather than avoiding an attack where I’m giving out tokens. If I have an inline token challenge, shouldn’t it have the same security property if I bounce that back to the entire issuance path, and relying on the attester.

Philipp: Tokens are prefetched, key pairs are generated asyc ahead of time. When the challenge happens, one of those key pairs are used to respond to that challenge. 

Tommy: Do we think it’s ok to do this for latency? I think it’s fine.

Chris:Yes, primarily about latency reduction. The private keys can’t leave the device

Borbala: The primary reason is latency, yes. The secondary reason is that it helps with the privacy property. By the time of the server call, the system doesn’t yet know where it’ll be used. So the server doesn’t know the identity of the relying party.

Tommy: Reducing timing attacks?

Chris: The issuer will not learn what origin the token is for, in the basic privacy pass case the issuer also does not learn what origin the token is for because of the blind signing. So I would not say that this improves the privacy. It also makes it harder to pop tokens off of devices. With PP today tokens are just sitting in memory, but with the enclave the only way to get a token off a device is to actively challenge it.

Mariana: this assumes you can’t put the PP tokens in an enclave

Philipp: The whole token fully formed leaves the enclave at some point, so I can just snoop on that path.

Chris: Being able to challenge a client for a token and get a response can be done whether you use the regular PP approach or you locally issue them,

Tommy: Today to be able to pre-cache tokens, they cannot be bound to a particular context. So I think it makes it incrementally harder because we get improved latency properties while still have challenge properties tied to the token. 

Chris Wood: re token signing keys - earlier we were talking about single use/multi-use. This folds into another question. The simple mental model is that they are single use, but we’ll get to the re-use question in a moment

Brian: As well as lowering latency, it gives clients the ability to create tokens that work well with specific interactions. 

Mariana: Not sure I understand this point. With either of the 2 types of tokens this can be done.

Brian: It seems like if you get a bag of tokens from someone, it’s your bank account and you’re out when you’re out. If you can generate tokens, you can make decisions about how to generate tokens 

Mariana: This will be discussed next, multi-use tokens.

Chris: I think reuse would be fine if the scope of the reuse is under the control of the user. Compared to cookies, If I want to flush my cookies it should have the same effect on any tokens. I would prefer they not do this, but a user agent could implement this. If tokens persist across sessions that seems like a pretty significant regression. I recognize this is in conflict with the desire to implement rate limiting (i.e. users shouldn’t be able to flush their state and reset their rate limit)

Philipp: It still allows us to have some cap with what is available to the device. WE have a slow device integrity check and we can control how many tokens are issued. And it’s up to the site how many times you expect to see the same token. Anything that requires exact counting will require some roundtrip

Tommy: One clarification: Is the intent that when we clear browser data we will reset tokens or no?

Philipp: The tokens should be scoped to the cookie lifetime.

Tommy: I don’t see it being harmful, but wondering about the value. Today, with our implementation of PP, we don’t re-use it. But on the same TLS connection, we’ll ignore multiple challenges sent in the same minute. IF anything, it looks like an attack (weird harvesting behavior). Since you’re in the same session, you don’t need additional challenges. Even for a cookie scenario, if you’re concerned about someone sharing cookies, if you’ve already spent the token, don’t you want a new challenge?

Philipp: The work with the secure enclave happens on every request. 

Brian: Does this imply that during a session I can share multiple tokens with a 3rd party?

Phillip: Not sure about multiple tokens/multiple partners. But you should be able to verify the public key material, signed by the correct issuer. That verification of the signature chain can be done on the service/website requesting. 

Chris: One thing that might not be clear is that when the server asks the client for a token, a set of origins can be included. If a token is requested for a.com, it can only be redeemed for a.com in the PP scheme.

Brian: Presumably you could construct a list of partners with which you work?

Chris: Yes, you can construct what information is in that set of origins. A.com & B.com could agree to accept tokens from one another as long as they issue challenges in the same way.


Steven: Question for Joseph re PP. This runs counter to the idea of linkability in PP - the idea that you can’t link at all.

Joe: This runs counter to the goals of privacy pass, and is outside the charter. Wouldn’t say this couldn’t be done - but would need to have a discussion within PP about if this is something we are willing to take on. IETF meetings in the next few weeks would be a great opportunity to discuss.

Steven: If the chairs are happy about having that discussion there, I think that would be good.
Joe: The working group is keen on PP being used and usable - so if this is a requirement, would love to discuss.

Tommy: I would hope it would be fine to discuss it. Whether or not PP wants to standardize and produce a document that allows linkability is a different question. We are trying to set up an architecture that can be expanded on in private implementations. For transparency on our end, there are some cases where we have been talking about ways to identify and prevent abuse. It’s particularly difficult when you have to rely on random websites to report abuse correctly. Say some party on a server side is really tested, it becomes easier. 

Philipp: I’d be happy to prepare some materials. Also signal quality, some websites will be more specific than others.

Mariana: Want to point out that linkability will also depend on multi-use v single-use of the credentials. Adding additional properties of linkability for multi-use may have considerations for privacy properties

Chris: I want more clarity on what linkability means in this context. One of the proposals introduces an auditor, an entity in the feedback look that helps break linkability of client identity from origin, while also providing transparency for the feedback look actually being exercised. The origin isn’t able to break fundamental privacy goals. I’m not sure I agree with the claim that this is out of scope of the charter, but it depends on the specific solution - who learns what along the way. It’s possible to build something like this which achieves the functional properties while still privacy preserving. 

Nick: You talked about a good device being marked by an attester as bad. Attester wants to know that. Why do we need something in the protocol to handle that? The client can reach out to the attester directly if there is a problem.

Philipp: For false positives there is a user opt-in path where the user can get support from the attester. 

Nick: Not sure how often the details will matter for the false-negative.How much context do you need? If the origin is reporting x% of the attestations are false, isn’t that a good start

Philipp: some origins might maliciously over-report. Some thresholding could be done in an automated fashion. There’s also all of the context. Looking at properties of the user behavior that the antiabuse team can dig into to give the attester more information about the kind of abuse.

Nick: You can always just give all that information to the attester in a side channel.

Philipp: We want to discourage collusion between attester and websites. 

Philipp: How does the attester combine what they’re hearing with the actual attestations. We want to prevent collusion in the normal case, but we want to govern the linking of actual tokens

Nick: You would still have to share information to link up compromised devices.

Philipp: How do you know what attestations to look into?

Nick: And you might not know, if you got this labeling data

Vinod: The feedback loop is important, but the architecture was separating these rules consciously. The notion of having a trusted 3rd party helps with reconciling false positives/negatives. Entities can still maintain boundaries between each other.

Philipp: Want to help folks for tee’ing up the next sections! This helps bring us to talking about what a healthy ecosystem looks like.

Vinod: We cannot keep the ecosystem closed where only certain attesters are able to participate. Like what the FIDO alliance does for trusted computing hardware. Can we create criteria that are independently verifiable?

Philipp: Great question - lots of different ways to solve. FIDO alliance is one way. Another way is that within the feedback loop, there’s a way to origins to have some idea of attester quality. Feedback can help color the attester reputation

Brian: Attesters have a privileged relationship with device users. We would like to enable new issuers to come online. Allow clients to sign up with different issuers?

Philipp: We’ve thought about how to empower issuers, but a lot tdb. Can attester run in a trusted environment like a TEE? Maybe TEE + multiparty. Really you should just be proxying things between two parties. 

Philipp: What do we think about the amount of entropy and how comfortable we are with it?

