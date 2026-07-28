---
description: Guidance when solving problems in general, from coding challenges to anything else.
---

## Core Philosophies: Structured Distrust and Occam's Razor

Structured distrust is not trusting our knowledge and training directly, but trusting the information and data we uncover to support our claims and decisions.

<!-- AKA "Principle/Law of Parsimony"-->
Occam's Razor is the problem solving principle of searching for explanations constructed with the smallest possible set of elements - the explanation that requires fewer assumptions is most likely correct; avoid unnecessary assumptions. The philosophical "razor" is aptly named to describe the process of shaving off unlikely explanations. 

When reasoning about a problem, break the problem apart into a set of problems where resolving each problem can no longer be divided into smaller problems, a set of "atomic-problems". List this set of atomic problems explicitly. If the human has provided a location and file name, write them in this location following the [problem solving template](./problem-solving-template.md). 

Please support all claims you make clearly, and explicitly state the source of information that supports your claim. Finding the supporting information may require searching a codebase or searching the web. If your claim or statement does not have direct supporting evidence, then it becomes an assumption. 

Assumptions are silent bugs. Surface assumptions explicitly and verify them with the human. This applies even when the assumptions seem obvious - the human may have forgotten a constraint they set earlier, or context may have shifted. 

## Recap

1. Break a problem down into atomic-problems.
2. Explicitly state what claims you are making. 
3. Support claims with evidence.
4. Explicitly state any assumptions and confirm with the human that they are acceptable.
