# UX User Flow – Multi-Party Alliance (Tempo)

This document describes the core user flow of the **Multi-Party Alliance** feature, as defined in the Catalyst proposal.  
The scope is limited to alliance creation, membership, proposal submission, internal voting, and execution of mandates on-chain.  
This satisfies the **acceptance criteria** of M1: UX/UI design documentation is available and traceable in the repository, and can serve as **evidence** for delivery.

---

## 1. Sequence Diagram – User Interactions

```mermaid
sequenceDiagram
    autonumber
    participant U as User (DRep / ADA Holder)
    participant AL as Alliance Platform (Tempo)
    participant DR as DRep Representative
    participant CH as Cardano Governance (On-chain)

    U->>AL: Create Alliance (define rules, purpose)
    AL-->>U: Alliance created

    U->>AL: Browse and Join Alliance (meets criteria)
    AL-->>U: Membership confirmed

    U->>AL: Submit Proposal
    AL-->>U: Proposal published

    alt Internal Vote
        AL->>U: Open vote (For/Against/Abstain)
        U-->>AL: Cast vote
        AL-->>AL: Tally votes, check quorum/threshold
    end

    alt PASSED
        AL->>DR: Issue mandate (binding)
        DR->>CH: Cast on-chain vote
        CH-->>AL: On-chain receipt (tx hash)
    else FAILED
        AL-->>U: Proposal rejected
    end
```

## 2. State Diagram – Proposal Lifecycle

```mermaid
stateDiagram-v2
    [*] --> Draft
    Draft: Proposal drafted by member
    Draft --> Discussion: Published to alliance board

    Discussion --> Voting: Move to internal vote

    Voting: Members vote (For/Against/Abstain)
    Voting --> Decision: Tally + quorum/threshold

    Decision --> Mandated: If PASSED
    Decision --> Failed: If FAILED

    Mandated: Mandate issued (binding instruction to DReps)
    Mandated --> OnChain: DRep executes on-chain vote

    OnChain: On-chain transaction recorded

    Failed --> [*]
    OnChain --> [*]
```
