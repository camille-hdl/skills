---
name: data-modeling
description: "Data modeling - translate a conceptual domain model into a data model: classes, properties, attributes, tables, rows. Use when designing a new data structure from a domain: classes, entities, attributes, relationships, or a database schema."
metadata:
  source: "William Kent, Data and Reality, 3rd edition, with commentary by Steve Hoberman (Technics Publications, 2012)"
---

# Data Modeling

Use the `domain-modeling` skill if available. If it is not, suggest the user install it: https://github.com/mattpocock/skills/blob/main/skills/engineering/domain-modeling/SKILL.md

Data modeling is the process of eliciting business requirements and organizing the data to produce a data model.
Data modeling happens downstream of domain modeling: it helps you translate the conceptual domain model into the physical technical solution (classes, properties, attributes, tables, rows, etc.).

A data model is a set of symbols and text that precisely explains a subset of real information.
It is a wayfinding tool.
A data model is judged by its usefulness, and is not to be mistaken for the true structure of information. "The map is not the territory."

Scope and purpose are the two limits that make shared meaning achievable.
Scope is the number of viewpoints to reconcile; purpose is the task for which they need to agree.

Before designing a new data structure, make sure you have a clear idea of what that information is like, and a good grasp of the semantic problems involved:

- **Oneness**: what is "one thing"? Oneness means coming up with a clear and complete explanation of what we are referring to.
- **Sameness**: when do we say two things are the same, or are the same thing? How does change affect identity? Sameness means reconciling conflicting views of the same term.
- **Categories**: what is it? In what categories do we perceive the thing to be? What categories do we acknowledge? How well defined are they? Categories means assigning the right name to this term and determining whether it is an entity type, a relationship, or an attribute in the data model.
- **Existence**: are the things modeled real? How real? For how long?

Write down how each resolved distinction maps to the representation you choose, in the design document the project already uses: a spec, a ticket, or an ADR, for example. Not in a separate data model document: it would drift from the implementation.

## Naming

A name is a symbol for an idea.

**Uniqueness, scope, and qualifiers**: what is the scope of uniqueness?
Whether a name refers to one thing or many frequently depends on the set of candidates available to be referenced. This set of candidates is a "scope", and it is often implicit in the environment in which the naming is done.
Scopes are often nested, and we often employ a mixed convention: a larger scope is left implicit, but a sub-scope within it is explicitly specified. This is partial qualification.

## Relationships

A relationship is an association among several things, with that association having a particular significance.
The **reason** is an important part of the relationship: identifying the pair of objects involved is not enough.

**Degree, domain, and role**: a relationship can be specified as an unordered set of unique role names. The number of role names is the degree of the relationship. A domain is specified for each role.
