---
layout: base.njk
title: OSB-1 Product Realization Programme
order: 90
---

# OSB-1 Product Realization Programme

**Document type:** Development memorandum  
**Status:** Experimental  
**Associated product:** OSB-1 Optical Signature Beacon  
**Owning organization:** General Interface Systems Corporation

## 1. Purpose

OSB-1 began as a deliberately small engineering problem: construct a compact infrared beacon capable of presenting a persistent optical identity to an autonomous observer.

The technical problem is modest. Producing a finished physical product is not.

A product requires requirements, research, design decisions, component selection, procurement, firmware, electronics, mechanical construction, testing, documentation, revision control and repeated physical verification. In a small organization, the limiting resource across all of these activities is frequently human attention rather than technical possibility.

The OSB-1 Product Realization Programme therefore asks a broader question than how to build an infrared beacon:

> **How much of the process required to turn an idea into a physical product can be delegated to an organization of software agents?**

OSB-1 serves simultaneously as the product being developed and as the reference problem against which that organization can be evaluated.

## 2. The Product Is the Test

The objective of the programme is not autonomous software development for its own sake.

A system capable of creating issues, writing code and reviewing pull requests is useful, but it has not necessarily demonstrated an ability to produce anything outside its own software environment.

OSB-1 provides a concrete external objective. At the end of the process there must be a physical device which emits the required optical signature, can be observed and verified, has a known hardware configuration, runs known firmware and is accompanied by sufficient documentation to reproduce and understand it.

This makes the success criterion unusually resistant to optimistic interpretation.

The beacon either exists or it does not.

## 3. Product Realization as an Organizational Problem

GISC treats product realization as a collection of responsibilities rather than as the work of a single universally capable agent.

Different participants may possess radically different capabilities, knowledge, memory and authority. A participant able to reason deeply need not have access to external information. A participant with extensive documentation and web access need not be capable of sophisticated reasoning. A mobile robotic participant may understand very little about electronics while being uniquely able to inspect the physical environment.

The organization is expected to obtain useful behavior from these differences rather than attempting to eliminate them.

A participant should know what another participant can contribute without necessarily knowing how that capability is implemented.

## 4. Resident Instances

The Resident architecture provides a possible foundation for persistent software individuals operating within a bounded environment.

A Resident instance has an identity and an explicitly defined view of the world. Depending on its purpose it may have a long-lived session, local long-term memory, sensors, communication channels, physical capabilities or access to specialist information sources.

Different Resident instances need not be symmetrical.

Examples contemplated by the programme include:

- a primary Resident that experiences the local environment over time and develops persistent knowledge about it;
- a high-reasoning Resident with no persistent memory and no information source beyond the context explicitly supplied to it;
- an information-retrieval Resident with extensive access to documentation and external sources but intentionally modest reasoning capability;
- a creative Resident optimized for generating unusual or entertaining possibilities without being granted authority to execute them;
- a mobile robotic Resident capable of physically exploring the environment and performing bounded actions;
- specialist Residents concerned with memory consolidation, behavioral observation, cost accounting or safety monitoring.

These are organizational roles, not requirements of OSB-1 itself. Their value is measured by whether they help the organization make progress toward real engineering outcomes.

## 5. Physical Representation

A Resident participating in the local organization should have a physical representation.

For a robotic Resident this is naturally its mobile platform. For a stationary or primarily cognitive Resident, physical representation may be no more than a small display showing text, an expressive face or status information.

The representation does not need to expose the implementation of the underlying model. Its purpose is to give the individual an observable presence in the same bounded world occupied by the other Residents and by the Owner.

This produces a useful conceptual distinction between a background software service and an inhabitant of the system's world.

A search service may be a tool. A Librarian with a location, identity, communication behavior and representation is an actor.

## 6. Communication Rather Than Universal Tool Access

Where practical, specialist Residents should be approached as other actors rather than flattened into functions of a single central agent.

A primary Resident might ask a mobile Resident to inspect a room, ask an information-oriented Resident to locate a datasheet, or ask a high-reasoning Resident to analyze a set of observations.

The recipient remains responsible for deciding how to satisfy the request using its own capabilities.

Conceptually:

```text
Primary Resident
    |
    +--> Research Resident: "Find the relevant component documentation."
    |
    +--> Reasoning Resident: "Given these measurements, what is most likely wrong?"
    |
    +--> Robot Resident: "Please inspect the workbench for the missing prototype."
    |
    +--> Creative Resident: "Suggest alternative enclosure ideas."
```

Communication relationships may themselves be restricted. Two Residents are not required to be able or willing to communicate directly. The resulting topology is part of the organization rather than an implementation accident.

This allows the primary Resident to acquire an important form of experience: learning whom to ask, what context they require and how reliable their contributions have historically been.

## 7. The Bounded World

The primary Resident is not intended to be a general-purpose gateway to all available information.

Its world is deliberately local: the Owner, other Residents, HomeOps, sensors, displays, robots, physical objects, local events and accumulated memories of those things.

A change of 0.4 degrees Celsius in a room may be insignificant to a general-purpose model. It may nevertheless be the most important event in Resident's world at that moment.

External knowledge can be introduced through explicitly designated participants or capabilities when required. This preserves a distinction between intelligence and experience.

A Resident may use considerable intelligence to understand its world while obtaining most new knowledge *about that world* by experiencing it.

## 8. Organizational Memory

A long-running organization requires more than conversational history.

Resident's long-term memory is intended to contain learned facts, observations, recurring patterns, relationships, preferences, anomalies and other durable knowledge about its bounded world. A specialist Memory Curator may inspect experience and propose or perform memory consolidation according to explicit provenance and retention rules.

This memory is distinct from model-provider session history and distinct again from GISC's engineering record in GitHub.

The three systems answer different questions:

- session history: what was this agent recently doing and discussing?
- Resident memory: what has this individual learned about its world?
- engineering history: why and how did GISC change the software and product?

OSB-1 development may depend on all three without treating them as interchangeable.

## 9. AgentController as the Engineering Control Plane

AgentController provides the software-development control plane through which engineering needs can become durable work.

An idea is triaged. More complex work can be investigated before implementation is authorized. Approved changes are implemented in isolated branches/worktrees, subjected to repository-defined verification and published as pull requests. Independent review examines the exact proposed revision before human merge.

This is deliberately more structured than giving an autonomous agent write access to every repository.

Most importantly, the actor identifying a problem does not need the ability to implement its solution.

A Resident may eventually report:

> "I repeatedly fail to distinguish these two observations and need a more reliable way to compare them."

AgentController can convert that evidence into investigation and software work without requiring Resident to understand its own implementation.

The same process can operate on AgentController itself. Self-improvement proposals are permitted; bypassing the development control plane is not.

## 10. Observation and Improvement

A future Observer Resident may analyze operational behavior across the organization.

Its concern is not primarily the contents of individual conversations but empirical behavior: unnecessary wakes, failed actions, repeated questions, latency, token consumption, tool failures, unproductive specialist consultations, recovery incidents and changes in behavior following deployments.

This allows software changes to become experiments rather than merely completed pull requests.

```text
observe
   |
   v
identify limitation
   |
   v
create engineering evidence
   |
   v
investigate -> implement -> review -> deploy
                                   |
                                   v
                                observe
                                   |
                          +--------+--------+
                          |                 |
                       improved         regressed
                          |                 |
                         keep            rollback
```

The Resident requesting a change should not be the sole authority deciding whether the resulting behavior is better.

## 11. Resource Accounting

Specialist intelligence is not free.

Different Resident instances may use models with substantially different computational cost. A high-reasoning Resident that is consulted rarely may be economical; the same Resident used for every sensor event may not be.

A future accounting role may therefore observe resource consumption and expose it to the organization as another property of its environment.

This creates an engineering incentive for specialization. A relatively inexpensive primary Resident can decide when a difficult problem justifies consultation with a more capable specialist.

Cost is consequently not only an infrastructure concern. It can become information available to the system when deciding how to solve a problem.

## 12. Capability Governance

Not every Resident should possess every capability.

The creative participant that proposes unusual ideas need not be able to move a robot, modify HomeOps, deploy software or grant itself additional permissions. The research participant need not control physical devices. A reasoning specialist may have no persistent memory at all.

Capability enforcement belongs below the Residents themselves in a deterministic local policy layer.

A safety-oriented Resident may observe behavior, identify suspicious patterns and request restriction of another participant. The actual authority to grant, revoke or contain capabilities should remain in the policy/runtime layer rather than depending solely on the judgment of another language model.

No Resident should be able to increase its own authority merely by deciding that doing so would be useful.

This distinction permits increasingly autonomous behavior without requiring increasingly vague security boundaries.

## 13. Human Participation

The programme does not require removal of the human from every step.

The Owner currently supplies product intent, resolves ambiguous decisions, approves implementation, performs physical work and manual verification, and decides when software is merged or deployed.

The useful question is instead whether each recurring human responsibility can be made explicit.

When a human is required because the organization cannot perform a task, that limitation can itself become engineering information.

For example:

```text
Need: identify a component on the workbench
Current dependency: human inspection
Possible future capability: camera or mobile Robot Resident

Need: solder prototype hardware
Current dependency: human assembly
Possible future capability: automated assembly equipment
```

There is no requirement that every such dependency eventually be automated. Making it visible is sufficient to understand where the product-realization boundary currently lies.

## 14. OSB-1 as the Return Point

The infrastructure described in this memorandum is not the destination.

The destination remains OSB-1.

The programme becomes operationally interesting when the agent organization can return to the original engineering problem and make sustained progress on it: interpret requirements, identify unknowns, locate information, reason about alternatives, produce firmware, maintain documentation, request physical observations, analyze test results, detect failures and coordinate subsequent revisions.

The organization should eventually be able to say, in effect:

> "The next OSB-1 prototype is ready to be assembled. These are the components, these are the connections, this is the firmware, these are the expected measurements, and this is how the result should be verified."

At that point the infrastructure has demonstrated something more substantial than autonomous code generation.

It has participated in product realization.

## 15. Long-Term Objective

The programme may be considered mature when the resulting agent organization is capable of independently returning to the original engineering problem and coordinating the design, implementation, verification and physical realization of an Optical Signature Beacon.

The final physical step may initially remain human-operated. If the organization eventually identifies physical assembly as its principal remaining dependency, it is entirely acceptable for that observation to become another engineering problem.

The possibility that GISC Robotics might eventually construct equipment in order to manufacture the beacon is therefore not excluded by this document.

It is, however, considered substantially out of scope for Revision A.

## 16. Development Principle

The Product Realization Programme follows a simple recursive principle:

> **When the organization cannot progress because it lacks a capability, preserve the limitation as evidence and decide whether acquiring that capability is itself useful engineering work.**

This prevents infrastructure from becoming detached from its purpose. New agents, tools, memories, sensors, development automation and physical systems should ultimately be justified by the organization's ability to understand or act upon the product-realization problem.

The beacon is therefore both the beginning and the intended return point of the programme.

## 17. Success Criterion

The experiment succeeds when GISC's agent organization can take responsibility for enough of the engineering process that OSB-1 emerges as a documented, verified and physically realized product rather than a collection of ideas and prototypes.

Until then, development remains ongoing.
