**ATLAS STRATEGIC CONSULTANTS**

**INTELLIGENCE KNOWLEDGE BASE**

**PILLAR 4 --- AI-DRIVEN MATHEMATICAL PROBLEM SOLVING**

*March 2026 \| Caves Beach, NSW, Australia \| Version 1.1 \|
Classification: Internal Use Only*

**1. Purpose and Scope**

This brief documents the Pillar 4 intelligence reference for AI-driven
mathematical problem solving. The central event defining this pillar is
the publication of Donald Knuth\'s paper \'Claude\'s Cycles\' (February
28, 2026), in which Claude Opus 4.6 solved an open graph decomposition
conjecture that Knuth had been working on for several weeks. Knuth
opened the paper with \'Shock! Shock!\' and closed it: \'It seems I\'ll
have to revise my opinions about generative AI one of these days.\'

This pillar covers: the mathematical problem and its solution, the
agentic session methodology that enabled the result, the working Python
implementation (claude_cycles.py), the open even-m problem, and the
recommended platform and workflow for ongoing mathematical exploration
at Atlas. A platform upgrade note has been added at v1.1: Cowork (Claude
Desktop, macOS, Apple Silicon) is now the recommended environment for
extended exploration sessions, directly addressing the context
degradation failure mode documented in the Claude\'s Cycles paper.

> *Source: Knuth, \'Claude\'s Cycles\' (Feb 28 2026; rev Mar 2 2026).
> cs.stanford.edu/\~knuth/papers/claude-cycles.pdf. Verified March 6,
> 2026.*

**2. The Mathematical Problem --- Knuth\'s Digraph Conjecture**

**2.1 Problem Statement**

Consider the digraph G_m with m\^3 vertices (i,j,k) for 0 \<= i, j, k \<
m, and three directed arcs from each vertex: (i,j,k) -\> ((i+1) mod m,
j, k) \[i-arc\]; (i,j,k) -\> (i, (j+1) mod m, k) \[j-arc\]; (i,j,k) -\>
(i, j, (k+1) mod m) \[k-arc\]. This gives 3m\^3 arcs in total. The
problem is to decompose all arcs into exactly three directed Hamiltonian
m\^3-cycles --- three cycles that together visit every vertex exactly
once per cycle, and collectively use every arc exactly once.

Knuth had solved the m=3 case and sought a general construction for all
m \> 2. Filip Stappers empirically found solutions for 4 \<= m \<= 16,
establishing strong evidence that decompositions exist for all m. The
structural question --- finding a provably general rule --- was the open
problem.

**2.2 The Solution (Claude Opus 4.6, Exploration 31)**

Claude found the construction via a fiber decomposition insight. The key
observation: the quotient map phi(i,j,k) = (i+j+k) mod m maps all arcs
from fiber F_s to F\_{s+1}. The digraph is layered. Within each fiber,
the choice of which coordinate to bump depends only on i, j, and s ---
not on k.

Knuth\'s C program (direct translation of Claude\'s Exploration 31
Python program):

s = (i + j + k) % m

if s == 0: d = \'012\' if j == m-1 else \'210\'

elif s == m-1: d = \'120\' if i \> 0 else \'210\'

else: d = \'201\' if i == m-1 else \'102\'

Cycle c bumps coordinate d\[c\]: \'0\'-\>i, \'1\'-\>j, \'2\'-\>k

For the interior fibers (0 \< s \< m-1), the rule d\[c\] produces
coordinate (c+s) mod 3 --- the modular m-ary Gray code on page 299 of
TAOCP Vol 4A, which Claude independently derived and called a
\'serpentine pattern.\' The boundary fibers (s=0, s=m-1) use special
cases that handle wrap-around correctly for odd m.

**2.3 Verification**

Filip Stappers tested Claude\'s Python program for all odd m from 3 to
101, finding perfect decompositions each time. The Atlas
claude_cycles.py implementation independently verifies odd m=3 to 21
(all pass), with the \--max 101 flag reproducing the full Stappers test.
The implementation is a direct Python translation of Knuth\'s C program
from the paper.

**2.4 Knuth\'s Theorem and the 760 Decompositions**

Knuth proved the theorem formally and characterised the solution space.
A decomposition is \'Claude-like\' if the permutation d depends only on
whether i, j, and s are 0, m-1, or interior. The theorem states: a
Claude-like decomposition is valid for all odd m \> 1 if and only if
each of the three sequences it defines for m=3 is generalizable
(produces a Hamiltonian cycle for all odd m \>= 3).

Of the 11,502 Hamiltonian cycles for m=3, exactly 996 are generalizable
to all odd m \> 1. Exactly 760 of the 4,554 valid m=3 decompositions use
only generalizable cycles. These are the 760 \'Claude-like\'
decompositions valid for all odd m \> 1. Claude\'s construction is one
of them.

> *Source: Knuth paper, Section 3. 760 enumerated by exact cover
> computation using all 11,502 Hamiltonian cycles for m=3.*

**3. The Open Problem --- Even m**

The even-m case of the decomposition problem remains completely unsolved
as of March 2026. Knuth notes that m=2 was proved impossible by Aubert
and Schneider in 1982 (Journal of Combinatorial Theory B32:347-349). For
larger even m, Knuth writes: \'As part of exploration number 24, Claude
said that it had found solutions for m=4, m=6, and m=8; yet it saw no
way to generalize those results.\'

The even-m failure mode is structural. The interior fiber rule (c+s) mod
3 may still hold for even m --- the Atlas probe in claude_cycles.py
shows no arc collisions in the interior for any even m tested. The
breakdown occurs at the boundary fibers (s=0, s=m-1), where the
special-case rules that work for odd m do not cover even-m boundary
geometry correctly.

Knuth\'s account of Claude\'s breakdown is instructive: \'There after a
while it seemed to get stuck. In the end, it was not even able to write
and run explore programs correctly anymore, very weird. So \[Filip\]
stopped the search.\' This describes a known failure mode of LLM-based
mathematical exploration: context degradation over long sessions,
compounded by error accumulation when working at the edge of the
model\'s capability. The Cowork environment (v1.1 addition) and the
plan.md session discipline were both designed to mitigate this.

The even-m case is the priority open problem for Pillar 4. The
recommended next step is: for m=4, enumerate all valid d-assignments at
the 16 boundary vertices (s=0, s=3) using exhaustive backtracking,
compare to Claude\'s known SA solutions, and test whether any boundary
fix generalises to m=6 and m=8.

**4. Agentic Session Methodology**

**4.1 The plan.md Documentation Loop**

The session that produced the result used an explicit agentic discipline
imposed by Filip Stappers: \'After EVERY exploreXX.py run, IMMEDIATELY
update this file \[plan.md\] before doing anything else. No exceptions.
Do not start the next exploration until the previous one is documented
here.\' This is the plan.md documentation loop, and it is the required
standard for all Pillar 4 agentic mathematical exploration sessions at
Atlas.

The discipline serves three functions: it prevents the session from
losing progress when Claude encounters errors and restarts; it forces
the model to consolidate and name what it has learned before proceeding;
and it produces a traceable record of the exploration path that can be
resumed in a later session. Knuth\'s paper reproduces a summary of all
31 explorations, demonstrating that the final construction (Exploration
31) depended critically on observations made in Explorations 20, 21, and
30.

**4.2 Cowork as the Recommended Exploration Environment (v1.1)**

Cowork (Claude Desktop, macOS, Apple Silicon M1 or later) is now the
recommended environment for all extended Pillar 4 sessions. It runs in a
persistent local VM with direct filesystem access and MCP integrations.
Compared to terminal-based Claude Code, it eliminates the need to
re-establish session context between exploration runs and keeps the
plan.md file, explore scripts, and Claude context co-located in a single
persistent session. This directly targets the failure mode Knuth
documented: context degradation and error accumulation over long
sessions at the model\'s capability frontier.

Session startup discipline: open Cowork, navigate to the Pillar 4
working directory, read the current plan.md state, then begin the next
exploration. Do not begin a new exploration run without first loading
plan.md. Use Opus 4.6 for frontier exploration sessions where maximum
reasoning depth is required.

**4.3 Key Methodological Observations**

The Claude\'s Cycles session illustrates patterns that generalise to
other mathematical exploration tasks: iterative reformulation (the
problem was reformulated from graph decomposition to fiber decomposition
at Exploration 15, the critical pivot); failure documentation (14 failed
approaches are explicitly listed; each exclusion narrowed the search
space); and near-miss analysis (Exploration 27 found a construction that
worked for all m=3..9 with 3(m-1) conflicts, which was then proved
impossible in Exploration 29, redirecting to the final approach).

The session also demonstrates the limits: Claude could not produce a
formal proof (Knuth did that), could not generalise the even-m case, and
required repeated human intervention to keep documentation discipline.
The result is augmented mathematics --- human-guided AI exploration ---
not autonomous mathematics.

**5. Working Implementation --- claude_cycles.py**

The file claude_cycles.py implements the verified construction. It is a
direct Python translation of Knuth\'s C program. No external
dependencies are required.

python claude_cycles.py \# verify odd m=3..21, probe even m=4..12

python claude_cycles.py \--max 101 \# full Stappers test (all odd m to
101)

python claude_cycles.py \--even \# even-m probe only

python claude_cycles.py \--all \# both suites

The plan.md session log (same directory) documents the current
exploration state and planned next steps. Both files are treated as
version-controlled working documents, updated at the start and end of
every Pillar 4 session.

> *Desktop backup:
> /Users/atlas/Desktop/Atlas_Intelligence/Pillar_4_AI_Mathematical_Problem_Solving/*

**6. AI Platform and Tool Inventory**

The following platforms are directly relevant to Pillar 4 work. Claude
Opus 4.6 is the model that produced the Claude\'s Cycles result. Claude
Sonnet 4.6 is the current Atlas working model for iterative verification
and document generation. Cowork has been added at v1.1 as the
recommended exploration environment.

  --------------------------------------------------------------------------
  **Platform**            **Relevance to Pillar 4**             **Access**
  ----------------------- ------------------------------------- ------------
  Claude Opus 4.6         Anthropic hybrid reasoning model      Anthropic
                          released Feb 5, 2026. Enhanced        (API)
                          multi-step reasoning. Used by Filip   
                          Stappers in the Claude\'s Cycles      
                          session. Model string:                
                          claude-opus-4-6. Reserve for Pillar 4 
                          exploration sessions at the reasoning 
                          frontier.                             

  Claude Sonnet 4.6       Current Atlas working model           Anthropic
                          (claude-sonnet-4-6). 1M token context (API)
                          window in beta. Efficient for         
                          iterative coding, data extraction,    
                          and document generation across all    
                          four pillars.                         

  Claude Code             CLI agentic coding tool. Long-running Anthropic
                          autonomous sessions with filesystem   CLI
                          access. Recommended for extended      
                          mathematical exploration sessions     
                          requiring persistent context.         

  Cowork (Claude Desktop) NEW --- March 2026. Brings Claude     Claude
                          Code\'s agentic capabilities to the   Desktop
                          Claude Desktop app for knowledge      (macOS,
                          work. Runs locally in an isolated VM  Apple
                          with direct filesystem access and MCP Silicon)
                          integrations. Requires Apple Silicon  
                          (M1+) on macOS. Directly mitigates    
                          the context degradation failure mode  
                          documented in the Claude\'s Cycles    
                          session. Recommended environment for  
                          all extended Pillar 4 exploration     
                          sessions.                             

  PentAGI / BlacksmithAI  Multi-agent agentic frameworks        OSS / Docker
                          (Pillar 3) demonstrating hierarchical 
                          agent architecture relevant to        
                          mathematical problem solving.         
                          Long-term memory via Neo4j (PentAGI)  
                          relevant to session persistence.      

  Python + itertools      Reference implementation environment  Standard
                          for claude_cycles.py. Standard        library
                          library only. No external             
                          dependencies required.                
  --------------------------------------------------------------------------

**7. Reference Library**

  ----------------------------------------------------------------------------------------------------------------
  **Source**        **Date**   **URL / Location**                                         **Notes**
  ----------------- ---------- ---------------------------------------------------------- ------------------------
  Knuth,            Feb 28     https://cs.stanford.edu/\~knuth/papers/claude-cycles.pdf   Primary source. Full
  \'Claude\'s       2026 (rev                                                             proof, C program, 760
  Cycles\'          Mar 2)                                                                decomposition
                                                                                          enumeration, even-m open
                                                                                          problem statement.

  Knuth, TAOCP Vol  2011,      https://www.cs.stanford.edu/\~knuth/taocp.html             Modular m-ary Gray code
  4A                p.299                                                                 (the \'serpentine\'
                                                                                          pattern Claude
                                                                                          independently derived).

  Knuth, fasc8a     Ongoing    https://cs.stanford.edu/\~knuth/fasc8a.ps.gz               Hamiltonian paths and
  draft                                                                                   cycles draft. Contains
                                                                                          the original exercise
                                                                                          Claude solved. Monitor
                                                                                          for even-m additions.

  Aubert &          1982       J. Combin. Theory B32:347-349                              Proves m=2 case
  Schneider 1982                                                                          impossible. Foundational
                                                                                          impossibility result for
                                                                                          even m.

  arXiv cs.CO       Active     https://arxiv.org/list/cs.CO/recent                        Combinatorics preprints.
                                                                                          Monitor for even-m
                                                                                          progress or
                                                                                          generalisation attempts.

  Scholar Gateway   Active     https://semanticscholar.org                                Search \'Cayley digraph
  (MCP)                                                                                   Hamiltonian
                                                                                          decomposition\' for
                                                                                          related literature. Use
                                                                                          inline via MCP
                                                                                          connector.
  ----------------------------------------------------------------------------------------------------------------

**8. Open Problems and Next Steps**

The even-m case is the primary open problem. Three candidate approaches
are: (1) exhaustive backtracking over boundary fiber assignments for m=4
(16 boundary vertices, feasible by computer); (2) algebraic analysis of
why the odd-m boundary rules fail for even m --- the Gray code parity
argument likely breaks on even-length cycles; (3) monitoring arXiv cs.CO
for attempts by other researchers following the Knuth paper, which had
635,000+ views within hours of publication.

A secondary open direction is the symmetry question. Knuth notes that
none of the 760 generalizable decompositions have full cyclic symmetry
under the map ijk -\> jki -\> kij, though 136 of them are invariant
under one such rotation. Whether any even-m construction (if it exists)
could have cyclic symmetry is not known.

The Claude\'s Cycles paper is also a methodological template. Knuth
explicitly credits the plan.md discipline and the fiber decomposition
pivot as the structural innovations. Future Atlas mathematical
exploration sessions should adopt this framework for any problem
requiring more than 5 exploration iterations. The addition of Cowork at
v1.1 removes the primary technical obstacle to running such sessions
effectively.

**Document Information**

Prepared by: Atlas Strategic Consultants --- Gary Stewart, Lead
Consultant

Date: March 6, 2026 \| Status: Active --- Version 1.1 \| Classification:
Internal Use Only

Next Review: When even-m progress is made, new Knuth draft posted, or
further Cowork session discipline refinements identified.

Key event: Knuth \'Claude\'s Cycles\' (Feb 28 2026) --- Claude Opus 4.6
solves open Hamiltonian decomposition conjecture. Platform upgrade v1.1:
Cowork added as recommended exploration environment.
