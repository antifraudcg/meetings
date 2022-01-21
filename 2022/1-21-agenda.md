# January 21, 2022

## Logistics

12-1 PM EST / 9-10AM PST / 5-6PM GMT

## Agenda

* Chair Introductions (5 minutes)
* Charter Review (15 minutes)
* Attacker tooling and tactics: How scaled abuse works on the web (15 minutes)
* Related Work (3 minutes)
* Initial Work Items (15 minutes)

## Resources

* [Minutes](https://docs.google.com/document/d/1uM3vIFPwYdKgCVr7JqXf_g78WzWOj51qmGMk8JxQH8w/edit#)
* [Chair Slides](https://docs.google.com/presentation/d/1XAoj6Hq_DG1XHhI4yNs0ljNB44-AFY-TnJgSFAdBC0g/edit?usp=sharing&resourcekey=0-GxGUh1Q1wBTflpPcOgYbKw)

## Minutes

*   Current plan to have meetings every other Friday 12 PM ET / 9 AM PT / 5 PM GMT
*   Next meetings : Feb 4, 2022, Feb 18, 2022
*   #antifraud on w3c Slack: https://www.w3.org/wiki/Slack 
*   Charter Review ([draft charter](https://raw.githack.com/antifraudcg/antifraudcg.github.io/main/charter.html)) (15m)
    *   All please review and propose changes to the charter through Github
    *   Next meeting we can go through any remaining feedback and finalize the charter
    *   Changes since last meeting
        *   “Supporting user security, privacy, and accessibility” (instead of “improving”)
        *   Threat models, use cases, taxonomies can stay within the CG but there will be other proposals that are pushed out to other groups.
        *   “Fraud” vs “Abuse” wording - Discussion on https://github.com/antifraudcg/antifraudcg.github.io/issues/2
            *   [Missed point from Michael]
            *   Per: Fraud connected to something that’s illegal. The purpose of the group is not to discuss the difference between the two words. Abuse stays clear of the technicalities.
            *   Sanketh: I agree with the previous points in favour of abuse, we may want to consider stuff that may not necessarily conflict with local laws or terms of service.
            *   Philipp: Anti-abuse policy use cases lamped in - e.g. “people behaving badly” - fraud at its core includes deception.
            *   James: Dictionary definition “[Abuse](https://www.bing.com/search?q=define+abuse)” - use something for bad effect - misuse. We have to define what is abuse in that context. “[Fraud](https://www.bing.com/search?q=define+fraud)”: wrongful or criminal deception intended to result in financial or personal gain. Whichever we choose it needs to be clearly defined within the group context. Fraud has a clear definition, Abuse uses the word “bad” and is subjective.
            *   Brian: Suggest focusing on traffic vs misleading content to narrow definition.
            *   Borbala: Abuse will include content scraping, misrepresentation. Which definition would they fit? Badness categories of what we want to protect.
            *   Ian: Definitions looking into United Nations secretary personnel
            *   Vacha: Proving that something is fraud is a higher bar. We may not always be able to prove that something is fraud but we can tell it’s abuse.
            *   Jeffrey: +1 for Borbala’s point. Think of the different categories.
            *   Per: This group won’t define policies of what is fraud & abuse. The goal is to enable companies to “detect” it. The scope can be broad. There are cases of abuse we should be able to detect but wouldn’t be classified as fraud. We should be more inclusive. Better to have a scope that is a bit broader.
            *   Sameer: Fraud is very well defined in the payments context.
            *   Steven: We should decide where we want to draw the line. What sort of use cases and threat models are within scope. Maybe come up with an initial wording and we can later amend the charter.
            *   Brian: I would propose something similar. It’d be good though to have a good initial wording to guide the group as to what is in scope or not. The scope should be dictated by what we can actually achieve.
            *   James: Building on Per’s & Brian’s point. Let’s focus on the use cases first. For example, communication or financial fraud would push the group in a different direction.
            *   Aram: The name not the biggest concern. Most important to determine the use cases. We don’t have to say this is associated with a legal regulation. We want to build specific standards that will enable others to address their use cases.
            *   Tom: Misrepresentation might be a bit closer to what might be technically addressable.
            *   Continue discussion in the [Github Issue](https://github.com/antifraudcg/antifraudcg.github.io/issues/2)
        *   Scope restricted to web? https://github.com/antifraudcg/antifraudcg.github.io/issues/4
            *   Chris: [PATCG](https://www.w3.org/community/patcg/) focused on both web and mobile environments
            *   Brian: I had a question similar to that in patcg and it was suggested that w2c focuses on the client and IETF focuses on the server. So, we may have to find folks in other groups to take over the issue.
            *   Micheal: We may not have the membership to discuss non-web issues. Furthermore, non-web contexts may have different constraints.
            *   Aram: We are not excluding non-web technologies, but we consider them at the web interface. We do not remove them from context, but because of how they touch the web, we might have to get involved. For example, CTV may be in scope if it touches the web.
            *   Brian May: It would be useful to build a list of suggested usecases. Use Cases are typically a starting point for most groups.
            *   Per: I think webview is just a way to access content on the web, it may be through a browser or some other interface. If the user is using a browser or a webview, then it seems in scope. If it is pure server to server, we may not consider it in scope. We are only concerned with the end user's perspective.
            *   Sandro: There may be many instances where the same infrastructure is serving to browsers and connected TVs. So there may be a lot of overlap between these types of fraud, and we may want to include them.
            *   Brian May: Once we have a use case document, this may become clearer – we could identify instances which are web-only or cross domain.
            *   Continue discussion on [GitHub](https://github.com/antifraudcg/antifraudcg.github.io/issues/4).
*   Attacker Tooling and Tactics (15m)
    *   We, at Google’s Anti-Abuse team, protect Google products but also other projects.
    *   We have already discussed how abuse hurts users and companies.
    *   But we haven’t discussed how abuse is done.
    *   In this talk, I will discuss the tooling and tactics used by attackers.
    *   _Scaled abuse_ is something that is relatively cheap for an attacker to scale. Like having a way to do ad fraud with billions of clicks or lots of account compromise. This is in contrast to targeted abuse like industrial espionage.
    *   In scaled abuse, the attacker is limited in terms of resources but may still be profitable at scale.
    *   Scaled abuse is different from denial of service, the abuse here is usually motivated by money.
    *   A human organically interacting with the service as intended is not abuse.
    *   A human organically interacting with the service to harass users or other untended uses is abuse but not scaled abuse.
    *   We think of scaled abuse in three cases:
        *   1 = The attacker sets up specialized infrastructure
        *   2 = The attacker uses existing user’s infrastructure via malware or bad browser extensions.
        *   3 = The attacker sets up a hoard of humans who are tricked into participating in the scheme. This is different from malware because the user may want to allow the abuse via say disabling anti-virus software.
    *   We have seen attacker tooling evolve a lot from 2010. From basic python scripting to today’s state where attackers need to have real browsers and sometimes even real humans to generate diverse looking traffic.
    *   The attackers are motivated by money, and as the money scales, they are incentivized to improve their tooling.
    *   We are also seeing markets setup for selling specialized tooling to attackers, like tools to compromise accounts and tools to exploit compromised accounts.
    *   We see such tooling or tooling that can be used for that purpose even on places like GitHub.
    *   When we think about attacks carried from attacker controlled infrastructure.
        *   Device diversification is making a huge difference. Previously, it was easy for an attacker to launch attacks without thinking about diverse identities. Sometimes there exist browsers that inadvertently make it easy for abusers to do this.
        *   The genesis market recently got press coverage, it was a place to buy hijacked cookies and other resources to make it easy to pretend to be a honest user.
        *   On Device Scaling, we see abusers using modified automation frameworks, modified to evade detections. Cloud based virtualization is on the rise. Device farms are less common these days but we still see it in mobile spaces.
        *   IP Diversifications: seen widely through botnets and proxies.
        *   Piggybacking on good-user devices: malware may use a new session via say a headless browser; but more advanced malware (like bad browser extensions) may use the existing user sessions, making it especially hard to detect abuse. The role of browser extension stores is 
        *   Incentivized users: rise of incentivised user abuse, from users being paid to “like” posts to more complicated abuse.
    *   Takeaways:
        *   Abuse is non-stationary, attacker tactics are always evolving.
        *   Attackers use diverse techniques so we need diverse mitigations.
        *   Attacker tooling is quite advanced so we want to build robust defenses.
    *   Framing suggestion: three pillars for safety/anti-abuse.
        *   1 = Platform, what safety APIs can the web platform provide to help users. For example, app attestation or click attestations, hardware crypto binding. These make it easy to detect spoofed devices. It may be worthwhile to make a list of such APIs.
        *   2 = Monitoring, since anti-abuse is non-stationary, we may want to keep iterating on the signal we use. We should have principles on what is okay to monitor and what is not okay to monitor.
        *   3 = Developer Accountability, we should raise the bar so we see fewer bad browser extensions or bad apps.
    *   Brian May: The efforts to combat abuse seems in conflict to the efforts being made to address privacy and we’re going to need to “thread that needle”. 
    *   Borbala: The question is whether we can think of APIs that leads to a win-win in privacy and anti-abuse.
*   Related Work (3m)
    *   [IRTF PEARG](https://irtf.org/pearg)
    *   Privacy Principles : https://github.com/w3ctag/privacy-principles/pull/105 
    *   In the Web Payment Security IG we started work on risk assessment requirements related to 3DS (very drafty): https://github.com/w3c/wpsig/blob/gh-pages/3ds-reqs.md
    *   See https://github.com/antifraudcg/proposals/ 
*   Initial Work Items (15m)