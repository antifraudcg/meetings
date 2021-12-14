# December 14, 2021

## Logistics

12-1 PM EST / 9-10AM PST / 5-6PM GMT

## Agenda

* Introductions (5 minutes)
* Community Group Overview (10 minutes)
* CG Charter Process (15 minutes)
* Chair Nomination/Selection Process (10 minutes)
* Charter Discussion (10m)
* Initial Work Items (10m)

## Resources

* [Slides](https://docs.google.com/presentation/d/1HEEFZDZXYLn1wTgUQ1g9KTJ2mvAxeryk82iHcu-QNaU/edit?usp=sharing)

## Minutes

### Introductions (5 minutes)

1. Welcome from Steven, please use this Google doc to queue for questions and to sign in, the meeting minutes will be public.  This meeting and group are functioning under the W3C code of ethics.

### Community Group Overview (10 minutes)

1. Discuss problems in the Anti-Fraud space
2. Incubate solutions and APIs
3. Seeking a diverse set of participants

### CG Charter Process (15 minutes)

1. Goals, objectives
2. Mission, Scope
3. Draft up an initial charter based on this meeting and input from the mailing list - and then send out for additional feedback
    1. If necessary, can put it up for a vote where each organization gets one vote, but hopefully able to gain full consensus
4. ASK: Call for volunteers to help draft up the charter
    1. People are volunteering in the Zoom chat, Steven will collect those names
    2. Offering to help: Karan Khanna, Philipp Pfeiffenberger, Ian Jacobs; Offering to provide input: Joshua Ssengonzi, Per Bjorke
5. Consensus Building Process Overview
    1. Chairs will provide 7+ days for people to provide feedback and raise issues
    2. Goal is to reach consensus
    3. In case of sustained opposition without changes to the issue, and the proposer wishes to proceed, the chairs will hold a vote (with each org having one vote) in the CG. (votes are generally discouraged for substantive decision making)
6. Chair Responsibilities
    1. See deck for bulleted list
7. Nick's concern about the non-representative nature of voting - reinforces the importance of making as many decisions as possible by consensus
    1. Potential idea: create groups of stakeholders and ensure that each group has supporters for a proposal

### Chair Nomination/Selection Process (10 minutes)

1. Up to three chairs (up to one per organization)
2. ASK: Nominations by Jan 5th, 2022
    1. If more than 3 nominations, a vote will be held
3. Steven will send out an email template for how to express their candidacy for Chair

### Charter Discussion (10m)

1. Discussion of draft Mission
    1. Brad: do you want to have specific exclusions?
        1. Exploitation, Harassment, etc
    2. James: concerned about "those scenarios…" statement - proposes changing it to being mindful of user security…
    3. Brian: proposes defining fraud as "activity that actively seeks to deceive users"
    4. Per (from Google Anti-Abuse Ads): important to have a discussion around the Mission since it sets the foundation
        1. Proposes using the term "abuse" instead of Fraud
        2. Abuse could be financial, accidental, 
        3. Not only users that we want to protect, but also businesses - everyone in the ecosystem
        4. Need to balance Privacy, Security, Public Safety, Accessibility
    5. From chat:
        1. Michael Ficarra - I think the definition of fraud and unwanted traffic here is sufficient.
        2. Ian Jacobs - Not limited to users; could be attempts to defraud banks, for example.

2. Adoption process is similar to PrivacyCG: &lt;see slides>
    1. Anyone can make proposals, it is low friction.
    2. Once a proposal is made, it requires buy-in from at least one browser vendor to be adopted as a work item. This is to ensure that work is eventually implemented.
    3. If there is consensus, the proposal is adopted as a work item with the proposers as editors, typically.
    4. Once the work item matures, the editors work with the 
    5. Per Bjorke: Rather than keeping the deliverables as just APIs, we may want to educate and provide advice to other working groups on how to deal with abuse.
        1. +1 from Brad Chen in chat
    6. Response by Steven: That is a good point.
    7. Brian May: Are we considering things that may not involve a browser, like server-to-server communication.
    8. Response by Steven: A lot of w3c work is client based, but we can have a discussion on scope.
    9. Nick Doty: We may want to be open to work that is not Browser or API oriented but I acknowledge that this is what w3c focuses on. I don’t think we need to require the explicit browser buy-in to push a work item forward.
    10. James Rosewell: I think tight scope is key, this prevents going around in circles. I would advocate for tight scope and a clear success criteria.
    11. Brad Chen: While there is a technical part to anti-fraud, there is also the part of educating the public about fraud. If it is out of scope for anti-fraud CG under whose scope does it fall.
    12. James Rosewell: In the UK, this is the scope of the government; for instance, we currently have an online safety bill in consideration.
    13. Jeffrey Jaffe: Since there is no limit to the number of community groups, if people are interested in adjacent, but disjoint topics like education or server-to-server communication, it may be worth creating more community groups.
    14. RyanC: As an explicit example of topics that may be outside the client/API scope but work we should be looking at, the suggestions for wilful IP blindness and Apple’s private relay.
    15. Response from Steven: These proposals have a client component and may fall in scope through that. Perhaps the IETF should also have an anti-fraud group.
    16. Philipp Pfeiffenberger (over chat): In a world without strong client attestation, we will likely see some proposals that involve server-to-server comms. Proposals that are purely server-to-server may be more IETF-ish
    17. Brad Lassey (over chat): suggested text: "relevant implementer interest  (e.g. browser vendors for browser-based APIs)"
    18. RyanC (over chat) - I just wanted to mention things like "Willful IP Blindness" and Apple's "Private Relay" are things that certainly seem like they ought to be in scope.
    19. Michael Ficarra (over chat): I don't think "individuals defrauding other individuals online" should be in scope for this group (and especially not non-technical solutions to that problem). Maybe the "abuse" reframing will help with that
    20. RyanC (over chat) - We want to be able to 1) Detect use of techniques that are consider malicious (e.g. unsanctioned automation, misrepresentation) 2) Effectively enforce decisions to exclude entities from using a service with minimal privacy impact. 3) and probably other things
3. Meeting cadence: monthly vs. biweekly.
    1. Philipp Pfeiffenberger: I suggest starting with biweekly and later moving to monthly to capture the flurry of activity at the beginning compared to a more offline work once we get started.
    2. Brian May: A lot of w3c groups have adopted APAC friendly time.
    3. Response to Brian May: If there is bimodal distribution in the doodle poll, we can consider that.
4. Charter Scope. see slides
    1. James Rosewell: There is now a mature anti-fraud industry that curates and sells data that is used by publishers. We should try to not interfere with that market or force browser-based solutions.
    2. Philipp Pfeiffenberger: Could you clarify what you mean by non-browser-based clients?
    3. James Rosewell: Creating a browser-based API that provides a “is this human” may conflict with existing deployed measures for anti-fraud.
    4. Aram Zucker-Scharff: I recognize the existence of an anti-fraud vendor space, but I think that inevitably, they may be depreciated by technical solutions. I don’t think the fact that an idea exists does not mean that we should not depreciate or evolve them. Further, the privacy part of the mandate may also depreciate existing services offered by anti-fraud vendors.
    5. Per Bjorke: We should think about the challenges we are currently facing. We should try to be idealistic in the charter. For instance, saying that we can improve safety and improve privacy, may not be possible technically but we may be able to achieve it with non-technical, non-browser API solutions.
    6. James Rosewell: We currently have a choice in what anti-fraud vendor one chooses. Removing this choice may have an adverse impact on the market and bad for the web in general.
    7. Aram Zucker-Scharff: The choice may be a false one. The current solutions have their own problems even though they are currently deployed. We should not try to be limited by them.

Nick Doty (over chat): I think many of the multiple signals that James is referring to are signals that come from browsers/clients at the moment

Michael Ficarra (over chat): as a representative of an anti-fraud vendor, I am happy to have the technical means of our solution change dramatically based on the work of this group


### Next Steps

1. Steven: I will send out an email with a link to the minutes and further steps.
