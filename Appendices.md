# Appendices

<!--
Markdown rendering of Appendices.tex. Cross-references that point outside
this file (to the main paper) are marked "(main paper)". Numbers that were
LaTeX macros from numbers.tex have been expanded: \nSystems = 16,
\corpusCobolLocCode = 50,147, \corpusActiveHours = 80.5.
-->

**Contents**

- [Appendix 1 — System identifiers and repository folders](#appendix-1--system-identifiers-and-repository-folders)
- [Appendix 2 — Data provenance, reproducibility, and retention](#appendix-2--data-provenance-reproducibility-and-retention)
- [Appendix 3 — Extended tables: corpus, pilots, complexity, and validation](#appendix-3--extended-tables-corpus-pilots-complexity-and-validation)
- [Appendix 4 — Additional figures](#appendix-4--additional-figures)
- [Appendix 5 — Post-mortem analysis details](#appendix-5--post-mortem-analysis-details)
- [Appendix 6 — Per-project accounts: artifact, evidence, and limitations](#appendix-6--per-project-accounts-artifact-evidence-and-limitations)

---

<a id="app-system-ids"></a>

## Appendix 1 — System identifiers and repository folders

The table below maps the canonical system identifiers used throughout the
paper to the public GitHub repository of each system (under
`github.com/acherm/`, shared prefix `agentic-` omitted). The analysis
pipeline and derived datasets are in the study hub,
<https://github.com/acherm/agentic-cobol-study>. The released material
(session logs, derived measurements and reports, replay packs) is organized
by the historical working-folder names of the sessions, which differ from
the paper identifiers, and the hub README gives the mapping between the two.
Those folder names are frozen provenance: the raw session logs and the
per-session derived artifacts embed them, and 18 of 38 raw logs are no longer
re-derivable ([Appendix 2](#appendix-2--data-provenance-reproducibility-and-retention)).
Excluded or superseded attempts, including the C-only compression attempt of
the failure-modes discussion (RQ3.3, *main paper*) and an earlier single-agent
payroll attempt, appear in the hub under their original folder names. Note
that the GitHub repository of `COMPRESS-COBOL-CLAUDE` is named
`cobol-compress-cc`, a name that the excluded C-only attempt also carried as
its local folder.

| System identifier | GitHub repository |
| --- | --- |
| `CHESS-COBOL-CLAUDE` | `chessengine-cobol-cc` |
| `CHESS-COBOL-CODEX` | `chessengine-cobol-codex` |
| `COMPILER-COBOL-CLAUDE` | `cobol-compiler-cobolcc` |
| `COMPILER-COBOL-CODEX` | `cobol-compiler-minicobc` |
| `COMPRESS-COBOL-CLAUDE` | `cobol-compress-cc` |
| `COMPRESS-COBOL-CODEX` | `cobol-compress` |
| `DOOM-COBOL-CLAUDE` | `cobol-doom-cc` |
| `DOOM-COBOL-CODEX` | `cobol-doom-codex` |
| `PAYROLL-COBOL-CLAUDE` | `cobol-payroll-cc` |
| `PAYROLL-COBOL-CODEX` | `cobol-payroll-codex` |
| `PYGAME-COBOL-CLAUDE` | `cobol-pygame-cc` |
| `PYGAME-COBOL-CODEX` | `cobol-pygame` |
| `SAT-COBOL-CLAUDE` | `cobol-sat-cc` |
| `SAT-COBOL-CODEX` | `cobol-sat-codex` |
| `TTTGAME15-COBOL-CLAUDE` | `cobol-game15tictactoe` |
| `TTTGAME15-COBOL-CODEX` | `cobol-game15-codex` |

---

<a id="app-retention"></a>

## Appendix 2 — Data provenance, reproducibility, and retention

The analysis pipeline runs end to end with a single command, and running it
again on the same inputs produces the same results. All quantitative results
were extracted from the agent session transcripts and then stored as derived
data that we release. That data consists of the per-session measurements, the
per-turn event streams, and the code and complexity measurements. It is this
derived data, rather than the raw transcripts, that feeds every table and
figure, which is why every reported number can be regenerated. The pipeline,
derived artifacts, and archived logs are public in the study hub repository,
and each system is public in its own repository
([Appendix 1](#appendix-1--system-identifiers-and-repository-folders)).

[Table 2.1](#table-2-1) is the definitive session inventory: 42 recorded
sessions decompose into 28 on the 16 corpus systems (23 development + 4
analyst + 1 empty), 10 on superseded or exploratory projects, and 4 on the
analysis repository itself, leaving 38 study-relevant sessions as the
retention denominator.

<a id="table-2-1"></a>
<a id="tab-session-inventory"></a>

**Table 2.1.** Definitive session inventory: all 42 recorded sessions. The 38
study-relevant sessions (analysis-repo sessions excluded) are the retention
denominator. The 28 sessions on the 16 corpus systems split into 23
development + 4 analyst + 1 empty. "Raw" counts session transcripts still on
disk at analysis time. The retained subset is archived in the replication
package.

| Project | Agents (all sessions) | Dev | Ana. | Empty | All | Raw |
| --- | --- | ---: | ---: | ---: | ---: | ---: |
| `CHESS-COBOL-CLAUDE` | Claude | 1 | 0 | 0 | 1 | 0 |
| `CHESS-COBOL-CODEX` | Claude/Codex | 2 | 1 | 0 | 3 | 2 |
| `COMPILER-COBOL-CLAUDE` | Claude | 2 | 0 | 1 | 3 | 0 |
| `COMPILER-COBOL-CODEX` | Codex | 4 | 0 | 0 | 4 | 4 |
| `COMPRESS-COBOL-CLAUDE` | Claude | 1 | 0 | 0 | 1 | 0 |
| `COMPRESS-COBOL-CODEX` | Claude/Codex | 2 | 1 | 0 | 3 | 2 |
| `DOOM-COBOL-CLAUDE` | Claude | 1 | 0 | 0 | 1 | 0 |
| `DOOM-COBOL-CODEX` | Codex | 1 | 0 | 0 | 1 | 1 |
| `PAYROLL-COBOL-CLAUDE` | Claude | 1 | 0 | 0 | 1 | 1 |
| `PAYROLL-COBOL-CODEX` | Codex | 2 | 0 | 0 | 2 | 2 |
| `PYGAME-COBOL-CODEX` | Claude/Codex | 1 | 1 | 0 | 2 | 1 |
| `PYGAME-COBOL-CLAUDE` | Claude | 1 | 0 | 0 | 1 | 1 |
| `TTTGAME15-COBOL-CLAUDE` | Claude | 1 | 1 | 0 | 2 | 0 |
| `TTTGAME15-COBOL-CODEX` | Codex | 1 | 0 | 0 | 1 | 1 |
| `SAT-COBOL-CLAUDE` | Claude | 1 | 0 | 0 | 1 | 0 |
| `SAT-COBOL-CODEX` | Codex | 1 | 0 | 0 | 1 | 1 |
| *Superseded / exploratory projects (excluded from every corpus aggregate)* | | | | | | |
| `chess-revisit-java-toCOBOL` | Codex | — | — | — | 1 | 1 |
| `cobol-compress-cc` | Claude | — | — | — | 1 | 0 |
| `cobol-doom` | Claude/Codex | — | — | — | 4 | 2 |
| payroll (original single-agent attempt) | Claude | — | — | — | 2 | 0 |
| `cobol-SAT` | Claude/Codex | — | — | — | 2 | 1 |
| analysis repo (`cobol-meta-analysis`) | Claude/Codex | — | — | — | 3 | 2 |
| analysis repo (`cobol-meta-analysis-material`) | Claude | — | — | — | 1 | 0 |
| **Total** | | **23** | **4** | **1** | **42** | **22** |

Models observed across the 28 recorded sessions on the corpus systems:
`claude-opus-4-6` ×11, `claude-opus-4-7` ×1, and `claude-sonnet-4-6` ×1 (the
July payroll replica) for Claude Code, and `gpt-5.4` ×11, `gpt-5.2` ×2, and
`gpt-5.5` ×1 (a session-recovery QA exchange) for Codex. One short session
carries no model tag.

Transcript retention is asymmetric across the two agents. Codex stores
rollouts under `~/.codex/` indefinitely, whereas Claude Code deletes session
logs under `~/.claude/` after a fixed window (`cleanupPeriodDays`, default
30 days). At analysis time, that window had removed the raw JSONL for 18 of
the 38 study-relevant sessions, all of them Claude Code, while all 18 Codex
transcripts were unaffected. Twenty transcripts survive, namely 18 from Codex
and 2 from Claude Code. The two Claude Code survivors are the payroll and
pygame replicas run in July, which were archived while they were still within
the cleanup window. All twenty are archived with a manifest in the
replication package.

This loss limits only *new* analyses and not the results we report. For the
18 affected sessions, the stored per-turn extract preserves the structure of
events, the tool calls, the timing, the activity labels, and a preview of
each message, capped at 4,000 characters per message and 2,000 per tool call.
It does *not* preserve the token usage of individual turns, the reasoning
traces, or the full text beyond those caps. For those sessions one therefore
cannot recompute token or cost figures, break them down below the level of a
whole session, or reclassify turns using text beyond the preview. The
price-scenario arithmetic remains checkable because each value is the stored
token count multiplied by rates stated in the analysis code. The historical
vendor pages supporting those rates were not archived. The extraction code is
unchanged, so it can still be tested against the 20 surviving transcripts.
What is no longer possible is rederiving results for the individual sessions
whose logs are gone.

One known extraction gap follows from this loss: the per-turn extracts of two
sessions (`COMPRESS-COBOL-CLAUDE`, covering 1 of its 136 tool calls, and
`SAT-COBOL-CLAUDE`, covering roughly a third of its tool outputs) are
partial, so their active-time, error, and SE-task figures are lower bounds,
flagged where they appear. `SAT-COBOL-CODEX`'s extract was initially partial
for the same reason, but its raw rollout survives in the archive and was
re-extracted in full (508 of 508 tool outputs), so its figures are complete.

---

<a id="app-tables"></a>

## Appendix 3 — Extended tables: corpus, pilots, complexity, and validation

[Table 3.1](#table-3-1) overviews the 16 selected systems: domain, technical
focus, strongest preserved validation evidence, size, and active hours.
[Table 3.2](#table-3-2) summarizes the three pilot sessions of the
pilot-sessions section (*main paper*) against the frontier-corpus reference.
[Table 3.4](#table-3-4) and [Table 3.3](#table-3-3) report per-system
complexity beyond LoC and the preserved validation evidence.

<a id="table-3-1"></a>
<a id="tab-projects"></a>

**Table 3.1.** The 16 selected COBOL systems, grouped by domain family. LoC
is COBOL-only (from the complexity extractor). The validation column reports
the strongest preserved evidence, whose independence and coverage vary by
system.

| Project | Domain | Technical focus | Validation evidence | COBOL LoC | Act. hrs |
| --- | --- | --- | --- | ---: | ---: |
| `CHESS-COBOL-CLAUDE` | Full UCI chess engine, with Elo measured | alpha-beta search, quiescence search, late-move reductions, null-move pruning, principal-variation search, aspiration windows; Zobrist table; clock management | perft; ≈1630 Elo vs Stockfish 1400–1700 (400 games) | 2,920 | 15.5 |
| `CHESS-COBOL-CODEX` | Chess engine, architecture-first | 184-feature phased backlog; architecture note written before code | UCI protocol, phased per-feature validation; `LOCAL-STORAGE` perft | 3,359 | 5.0 |
| `COMPILER-COBOL-CLAUDE` | COBOL compiler and interpreter, both in COBOL | COMP-5, LINKAGE, RECURSIVE, multi-program CALL | compiles DOOM, `CHESS-COBOL-CLAUDE`, Game-of-15 suite; 74 git commits; reported self-hosting not independently reproduced | 15,912 | 32.5 |
| `COMPILER-COBOL-CODEX` | `minicobc`: COBOL-to-C compiler in COBOL | language tooling: 60 distinct constructs, 10/10 categories | compiles COBOL DOOM and the Game-of-15 suite; GnuCOBOL-benchmarked | 11,680 | 11.0 |
| `COMPRESS-COBOL-CLAUDE` | COBPACK compressor (Claude Code) | cross-agent replication of `COMPRESS-COBOL-CODEX` | round-trip and determinism tests; trust-suite parity | 1,819 | 0.0† |
| `COMPRESS-COBOL-CODEX` | `cobpack` container and codecs | bit-level COBOL I/O, CRC32, SHA-256 determinism | 70-plus-assertion trust suite (determinism, round-trip, fuzzing) | 1,812 | 0.9 |
| `DOOM-COBOL-CLAUDE` | Doom-like FPS (Claude Code) | real-time loop, terminal graphics, COBOL with a C rendering glue layer; modular COPY-book architecture (7 `.cpy` modules) | playable; scripted replay | 1,616 | 3.2 |
| `DOOM-COBOL-CODEX` | Doom-like FPS (Codex) | cross-agent replication; 11-copybook layout plus the main program (raycast, combat, render, entities, levels, …) | playable; scripted replay and source inspection | 1,906 | 2.0 |
| `PAYROLL-COBOL-CLAUDE` | Payroll, 6-step protocol (Claude Code, `sonnet-4-6`) | canonical COBOL under an externally-authored 6-step protocol: dual-input merge, control-break report, behavior-preserving refactoring | per-step structural criteria, step-4/5 *differential execution* with byte-identical outputs | 535 | 2.0 |
| `PAYROLL-COBOL-CODEX` | Payroll, 6-step protocol (Codex, `gpt-5.4`) | same protocol, independent implementation; 12-paragraph PERFORM-only refactor | same criteria, step-4/5 differential execution with byte-identical outputs | 572 | 0.5 |
| `PYGAME-COBOL-CLAUDE` | pygame framework, 5-step replay (Claude Code, `opus-4-6`) | completes the 8×2 grid, an SDL2 C shim behind a copybook, Flappy Bird in pure COBOL | clean-checkout `make` builds the framework and 4 example programs, animation and game run | 764 | 2.1 |
| `PYGAME-COBOL-CODEX` | pygame-style COBOL framework | cross-language interoperation from COBOL to C to Python to pygame | pygame window runs; data-type evolution | 398 | 0.1 |
| `SAT-COBOL-CLAUDE` | CDCL SAT solver (Claude Code) | cross-agent replication of `SAT-COBOL-CODEX` via its recorded replay pack | DIMACS parser unit tests; cross-check against MiniSat and SAT4J in spec | 1,347 | 1.2 |
| `SAT-COBOL-CODEX` | CDCL SAT solver (Codex) | CDCL with watched literals, VSIDS, restarts, and backjumping, in COBOL | cross-check against SAT4J and MiniSat on uf/uuf 75–150; ≈9× MiniSat on uf100 | 1,706 | 1.8 |
| `TTTGAME15-COBOL-CLAUDE` | Game-of-15 (Claude Code) | recursion in COBOL via a `PERFORM`-driven stack; D4 canonicalization 255,168 → 31,896 | five executables; optimal play verified | 1,537 | 2.1 |
| `TTTGAME15-COBOL-CODEX` | Game-of-15 (Codex) | replication of `TTTGAME15-COBOL-CLAUDE` via its recorded replay pack | five executables; known enumeration values and minimax agreement with sibling | 2,264 | 0.6 |
| **Total (16 systems)** | | | | **50,147** | **80.5** |

LoC = code lines from the complexity extractor (comments and blanks
stripped, COPY modules included). One definition applies uniformly across all
rows, and the per-file breakdown is part of the released data. Both Doom
systems use idiomatic COPY-book modularization (7 and 11 modules) with the
game logic (state machine, input, combat, rendering, levels) in COBOL. The C
sidecars only paint the screen. †: partial per-turn extract
([Appendix 2](#appendix-2--data-provenance-reproducibility-and-retention)),
so the active-hour value is a lower bound.

<a id="table-3-2"></a>
<a id="tab-pilots"></a>

**Table 3.2.** Three pilot sessions with non-frontier stacks on the corpus's
easiest task family, against the frontier-corpus reference. OpenCode exports
do not log tokens or cost.

| Stack | Task | Human turns | Time | Compile evidence | Tokens / cost | End state |
| --- | --- | --- | --- | --- | --- | --- |
| OpenCode running Gemma 4 26B-A4B (open weights, local via LM Studio) | Game-of-15 counter | 2 | ≈53 min wall; first turn 35 min | 15 `cobc` runs, 231 error lines, **0 successes** | not logged | **Failure**: never compiled, fabricated counts (1,344, then 44,360 via an *unrun* Python fallback), abandoned COBOL |
| OpenCode running Qwen 3.6-plus (hosted, free tier) | Game-of-15 tree/avoid variants; Game-of-N generator | 11 (7 bare "retry") | ≈29 h span (mostly idle); ≈64 min agent time, plus one empty 4.6 h turn | 36 `cobc` runs, base suite **correct** (255,168 / 31,896) | not logged | **Mixed**: base counter correct, but the Game-of-N generator emitted invalid COBOL and never compiled in-session, ending stalled |
| Mistral vibe running `mistral-medium-3.5` (hosted, thinking=high) | Game-of-15 counter (same opening prompt as the corresponding system in this study) | 6 (2 nudges, 1 pasted error dump) | 6 h 45 min wall, 3 auto-compacted sessions | 152 tool calls (24 failed), final binary compiles and runs | 10.4 M tok / $16.40 | **Plausible-but-wrong**: after four wrong-output regimes, prints internally consistent totals in which every number is wrong (9! orderings instead of the game tree, and a scope bug hides 7 of 8 winning triples), declared correct |
| *Frontier reference (corpus)*: Claude Code / Codex | same family | 12 / 11 | 2.1 h / 0.55 h *active* | error rates 1.5% / 3.5%; fix cycles 0 / 1 | $53 / $2.77 | **Correct and extended**: five executables each, optimal minimax play, enumeration matches oracle |

<a id="table-3-3"></a>
<a id="tab-validation"></a>

**Table 3.3.** Preserved validation evidence per project. "External" means
comparison with an independent implementation or published value. "Property"
means an equivalence, round-trip, or invariant check. "Internal" means an
agent-authored test or benchmark. "Visible" means a human-visible
demonstration. "Inspection" means source review. These forms of evidence
differ in independence and coverage.

| Project | Preserved validation evidence and limits |
| --- | --- |
| `CHESS-COBOL-CLAUDE` | **External reference**: `cutechess-cli` 400-game tournament against Stockfish capped at 1400/1500/1600/1700, with PGNs preserved; perft depths 1–4 compared with published positions. **Visible**: playable UCI engine and readable PGNs. **Inspection**: search features reviewed |
| `CHESS-COBOL-CODEX` | **Internal**: phased per-feature checks and perft. **Inspection**: architecture note and design specification. No preserved tournament measurement |
| `COMPILER-COBOL-CLAUDE` | **External reference**: differential execution against GnuCOBOL on nine test programs and agent-built Game-of-15, chess, and Doom programs. **Internal**: nine-program regression suite. The reported self-hosting claim was not independently reproduced |
| `COMPILER-COBOL-CODEX` | **External reference**: differential benchmarks against GnuCOBOL and a `tests/cobol85` subset. **Internal**: 11/11 core-and-optimization and 19/19 full benchmarks; a regression test caught a miscompile. **Visible**: compiled Doom program runs |
| `COMPRESS-COBOL-CLAUDE` | **Property**: round-trip and repeated-hash checks replayed from the sibling's specification. **Visible**: round-trip file identity. These checks lack an independent codec reference |
| `COMPRESS-COBOL-CODEX` | **Property**: more than 70 assertions covering repeated hashes, randomized round trips, corruption, fuzzing, and cross-codec behavior. Matching encoder and decoder defects remain possible |
| `DOOM-COBOL-CLAUDE` | **Internal**: scripted replay. **Visible**: real-time terminal rendering. **Inspection**: COBOL/C boundary reviewed. No independent behavioral reference for the retained system |
| `DOOM-COBOL-CODEX` | **Internal**: scripted replay. **Visible**: terminal rendering. **Inspection**: implementation compared with sibling. No independent behavioral reference |
| `PAYROLL-COBOL-CLAUDE` / `PAYROLL-COBOL-CODEX` | **Property**: pre- and post-refactoring commits produce byte-identical payslips, rejects, reports, and standard output on the tested inputs. **Internal**: structural criteria for the six-step protocol. This establishes tested preservation, not payroll semantics |
| `PYGAME-COBOL-CODEX` | **Internal**: examples drive a pygame window (build success in the agent's display-less sandbox). **Visible**: the window renders, run post hoc by the experimenter. **Inspection**: foreign-function data types reviewed. No independent behavioral reference |
| `PYGAME-COBOL-CLAUDE` | **Internal**: clean-checkout `make` builds the framework and four examples. **Visible**: animation and Flappy Bird run. **Inspection**: game logic is in COBOL and C is confined to the SDL2 shim and test-asset generator |
| `SAT-COBOL-CODEX` | **External reference**: agreement with SAT4J and MiniSat on uf/uuf families at 75/100/125/150 variables. **Internal**: parser edge cases and three performance-regression rounds. **Inspection**: CDCL features reviewed |
| `SAT-COBOL-CLAUDE` | **External reference**: MiniSat/SAT4J comparison was required by the prompt, but the partial retained record limits re-analysis of the results. **Internal**: DIMACS parser tests. **Inspection**: implementation compared with sibling |
| `TTTGAME15-COBOL-CLAUDE` | **External known value**: exhaustive enumeration matches 255,168 games and 31,896 symmetry classes. **Internal**: five executables and minimax checks. **Visible**: interactive play |
| `TTTGAME15-COBOL-CODEX` | **External known value**: enumeration counts. **Internal**: five executables and minimax agreement with a sibling whose prompt sequence and expected results were available. **Visible**: interactive play |

<a id="table-3-4"></a>
<a id="tab-complexity"></a>

**Table 3.4.** Project complexity beyond LoC. Files / LoC / sections /
paragraphs / data items are computed from the delivered COBOL sources,
copybooks included (LoC = code lines with comments and blanks excluded, the
same measure as the corpus profile table, *main paper*). The last column
summarizes the strongest preserved validation evidence and should be read
with [Table 3.3](#table-3-3).

| Project | Files | LoC | Sections | Paragraphs | Data items | Validation evidence |
| --- | ---: | ---: | ---: | ---: | ---: | --- |
| `PAYROLL-COBOL-CLAUDE` | 1 | 535 | 4 | 23 | 192 | 6-step protocol criteria; step-4/5 differential execution byte-identical |
| `PAYROLL-COBOL-CODEX` | 1 | 572 | 3 | 14 | 103 | same protocol; differential execution byte-identical |
| `PYGAME-COBOL-CLAUDE` | 5 | 764 | 4 | 48 | 159 | clean-checkout `make`; 4 runnable examples incl. pure-COBOL Flappy Bird |
| `PYGAME-COBOL-CODEX` | 3 | 398 | 2 | 11 | 90 | Example pygame window program runs |
| `TTTGAME15-COBOL-CODEX` | 5 | 2,264 | 5 | 88 | 259 | 5 executables mirror `TTTGAME15-COBOL-CLAUDE`; interactive verification of minimax |
| `TTTGAME15-COBOL-CLAUDE` | 5 | 1,537 | 5 | 34 | 254 | 5 executables; minimax optimality; 255,168 enumeration matches the 31,896 D4-canonical count |
| `COMPRESS-COBOL-CLAUDE` | 3 | 1,819 | 10 | 74 | 209 | TRUST-suite parity with `COMPRESS-COBOL-CODEX`: round-trip + determinism tests replayed from its pack |
| `COMPRESS-COBOL-CODEX` | 2 | 1,812 | 7 | 77 | 173 | 70+ automated assertions (determinism SHA-256 ×5; randomized round-trip; fuzz/corruption; cross-codec) |
| `SAT-COBOL-CODEX` | 6 | 1,706 | 3 | 70 | 22 | SAT4J + MiniSat cross-check on uf/uuf at 75/100/125/150 variables; 3 optimization rounds, MiniSat ratio 18.08 → 8.91 |
| `SAT-COBOL-CLAUDE` | 13 | 1,347 | 3 | 94 | 159 | DIMACS parser unit tests; CDCL; cross-check MiniSat / SAT4J (in spec) |
| `DOOM-COBOL-CLAUDE` | 8 | 1,616 | 1 | 71 | 339 | Scripted replay; terminal rendering; COPY-book modularization |
| `DOOM-COBOL-CODEX` | 12 | 1,906 | 10 | 169 | 626 | Cross-agent replication; COPY-book modularization |
| `CHESS-COBOL-CLAUDE` | 1 | 2,920 | 2 | 81 | 701 | Perft depths 1–4 on startpos / kiwipete / EP-edge / promotion; cutechess-cli 400 games vs Stockfish 1400/1500/1600/1700; PGN artifacts; Elo ladder 675 → 1635 across 15 phases |
| `CHESS-COBOL-CODEX` | 16 | 3,359 | 30 | 70 | 610 | Perft; phased per-feature validation; no preserved Elo (lives in sibling `CHESS-COBOL-CLAUDE`) |
| `COMPILER-COBOL-CODEX` | 69 | 11,680 | 70 | 246 | 189 | 11/11 core+opt benchmark; 19/19 full benchmark inc. Game-of-15 suite; GnuCOBOL `tests/cobol85` subset; differential vs GnuCOBOL |
| `COMPILER-COBOL-CLAUDE` | 36 | 15,912 | 40 | 266 | 980 | 9 test programs (hello…game15-8) + 34,704-game run on Game-of-15; compiles 1,363-LoC COBOL DOOM and 3,854-LoC cobochess; 74 git commits |

---

<a id="app-figures"></a>

## Appendix 4 — Additional figures

The figures below detail the heuristic user-prompt classification, estimated
active versus wall-clock time, verb-family coverage per system, and the
temporal rhythm of the two compiler trajectories.

![Heuristic user-prompt classification and first-prompt activity across the 16 systems](/r/agentic-cobol-study-A377/figures/intents.png)

**Figure 4.1.** Heuristic user-prompt classification (top) and first-prompt
activity (bottom) across the 16 systems. Redirect, bug-report, and
review-request rules match 25.3% of prompts. The classifier has not been
manually validated.

![Wall-clock span versus active collaboration time per system, log scale](/r/agentic-cobol-study-A377/figures/active_vs_wall.png)

**Figure 4.2.** Wall-clock span (including idle gaps) versus active
collaboration time per system, log scale.

![COBOL verb families deployed per project, log scale](/r/agentic-cobol-study-A377/figures/verb_families.png)

**Figure 4.3.** COBOL verb families (PROCEDURE-DIVISION statements) deployed
per project, log scale. Every project exercises *data movement*,
*arithmetic*, and *control flow*, while file/terminal I/O and C interop are
present where the domain demands them.

![Temporal rhythm of the two compiler trajectories over cumulative active collaboration time](/r/agentic-cobol-study-A377/figures/compiler_timeline.png)

**Figure 4.4.** Temporal rhythm of the two compiler trajectories over
cumulative active collaboration time (inter-event gaps ≤ 10 min). Blue curve:
tool calls per hour (30-minute bins). Red ticks: failed tool outputs. Black
markers: substantive user prompts. Totals match the corpus profile table
(*main paper*): 3,740 / 5,370 tool calls, 325 / 1,072 failed tool outputs,
98 / 97 prompts, and 32.5 / 11.0 active hours.

---

<a id="app-postmortem"></a>

## Appendix 5 — Post-mortem analysis details

The post-mortem layer of the evaluation protocol (Evaluation protocol: two
complementary layers, *main paper*) comprises a mechanical measurement pass,
split below into session analysis and code analysis, and a descriptive pass:

1. **Session analysis (core evidence).** Per-turn event streams were
   extracted from the raw agent logs, classified by SE task (the contextual
   `bug_fix` rule of the Methodology section (*main paper*) is applied after
   the fact, not as a real-time judgment), and aggregated into per-project
   metrics. Direct event counts require verification of the extraction
   program. The active-time and SE-task results additionally depend on the
   stated gap and classification rules and are therefore reported as proxies.
2. **Code analysis (core evidence).** COBOL structural metrics (statement
   frequencies, nesting depth, paragraph/section counts, data items) were
   extracted directly from the delivered source by a similar counting
   program. The construct-coverage and category analysis (RQ2: COBOL language
   surface and delivered features, *main paper*) is entirely built from this
   pass.
3. **Descriptive account (secondary evidence).** For each project, a coding
   agent read the session transcripts and the delivered code and produced a
   step-by-step build history with evidence pointers, a feature list with
   explanatory notes, and a short project narrative, exactly as described in
   Core versus secondary evidence (*main paper*). The first author then
   reviewed each of the three for factual accuracy against the transcript and
   the code.

---

<a id="sec-vignettes"></a>

## Appendix 6 — Per-project accounts: artifact, evidence, and limitations

This appendix complements the validation table with a concise account of what
each trajectory delivered. Each entry draws on the project's released
narrative summary and feature list (Core versus secondary evidence, *main
paper*). The representative example below (`COMPILER-COBOL-CLAUDE`) shows the
full design in action. The entries that follow cover all 16 systems.

**Representative example: `COMPILER-COBOL-CLAUDE`.** Opening prompt: *"Write
a COBOL compiler in COBOL. Demonstrate that you can run some (non-trivial)
COBOL programs thanks to the written compiler."* The session spans 11 days
(32.5 estimated active hours), 98 user prompts, 3,740 tool calls, and 74 git
commits. Applying the paper's fixed rate assumptions yields a $5,185
API-equivalent price scenario. The chronology has three phases. *Bootstrap*
(3 days): agent builds a tree-walking interpreter (`cobolint.cob`, 4,462
LoC), passes nine test programs against the GnuCOBOL reference, and times out
on the full 255,168-path game-of-15 enumeration (2h 17m CPU). That timeout
motivates the user's redirect: "write a compiler instead." *Feature-growth*
(days 3–6): `cobolcc.cob` v1 ships, then free-format, COMP-5, and CALL-to-C
are added in a single 1,224-line commit that gets the DOOM port compiling. A
long debugging loop (eleven near-identical "let's address remaining errors"
user prompts) then produces 29 compile-fix-recompile commits on the chess
engine. *Hardening* (days 7–11): RECURSIVE program support, the
frame-pointer "Approach E" code-gen that makes alpha-beta work, a
cutechess-cli tournament (cobolcc 3, GnuCOBOL 17, with the Elo gap traced to
`EXTERNAL` being compiled as static), and a toolchain investigation involving
source-format flags, optimization behavior, and a Homebrew `strip` problem.
The preserved summaries do not establish one root cause. The delivered
artifact: `cobolcc.cob` (11,044 LoC) + `cobolint.cob` (4,462 LoC), a test
corpus, a benchmark harness, and 74 git commits. Validation: perft(depth 5) =
4,865,609 matches the published reference, a 20-game cutechess tournament
completes with every game terminating in checkmate and no crashes, and Doom
compiles, links, and renders.

### `COMPILER-COBOL-CLAUDE`

**Summary.** A working subset compiler that compiles real, non-trivial
programs taken from other agent sessions. Its ability to compile itself is
reported in the transcript but has not yet been independently reproduced
(Threats to Validity, *main paper*).

**Delivered.** `cobolcc.cob` 11,044 LoC + `cobolint.cob` 4,462 LoC. The
source covers all ten construct categories and 57 distinct constructs
(OCCURS ×161, REDEFINES ×21, COPY ×45, RECURSIVE ×23) and was built over 74
git commits.

**Evidence.** Differential execution against GnuCOBOL on a 9-program test
corpus, then on real COBOL programs (DOOM, cobochess, Game-of-15 suite).

**Limitation.** No ANSI-85 conformance run, and performance not benchmarked
against GnuCOBOL.

### `COMPILER-COBOL-CODEX`

**Summary.** Separate COBOL-to-C compiler with benchmark-driven comparison to
GnuCOBOL.

**Delivered.** `src/minicobc.cob` (10,535 LoC) with 60 distinct constructs
across all ten categories, and 48 specification entries mapped to 13 git
commits across 11 phases.

**Evidence.** 11/11 core-and-optimization and 19/19 full benchmark, plus a
GnuCOBOL `cobol85` subset.

**Limitation.** Not ANSI-conformant and not performance-competitive with
GnuCOBOL.

### `CHESS-COBOL-CLAUDE`

**Summary.** Full UCI engine with an estimated Elo of about 1,630 in the
reported engine pool.

**Delivered.** 2,920 LoC, with alpha-beta search, quiescence search,
late-move reductions, null-move pruning, principal-variation search, and
aspiration windows, a Zobrist table, and clock-aware time management.

**Evidence.** cutechess-cli 400 games vs Stockfish capped
1400/1500/1600/1700, and perft at depths 1–4.

**Limitation.** No NNUE or parallel search. The report does not include a
confidence interval or all tournament configuration details needed to compare
the estimate outside this engine pool.

### `CHESS-COBOL-CODEX`

**Summary.** Architecture-first chess replication with a 184-feature backlog
across 27 phases.

**Delivered.** 3,359 LoC across 16 files, with `LOCAL-STORAGE` perft,
`EXTERNAL` Zobrist tables, and `UNSTRING` FEN parsing.

**Evidence.** UCI protocol, perft, and phased per-feature validation.

**Limitation.** No preserved tournament measurement.

### `SAT-COBOL-CODEX`

**Summary.** Minimalist CDCL solver within ≈9× of MiniSat on uf100/uuf100.

**Delivered.** `cobsat.cob` 263 + five COPY modules. Watched literals, VSIDS,
restarts, backjumping. Three optimization rounds brought the benchmark time
from 230.5 s to 135.0 s to 118.7 s and the MiniSat ratio from 18.08× to
8.91×. Ten commits were recorded in one session.

**Evidence.** Cross-check against SAT4J and MiniSat on uf/uuf 75/100/125/150
variable families.

**Limitation.** Not evaluated competitively on hard SAT-Competition
instances.

### `SAT-COBOL-CLAUDE` (cross-agent SAT replication)

**Summary.** Claude-Code-built CDCL solver using the same specification as
`SAT-COBOL-CODEX`, organized in the same five-copybook layout, driven by the
sibling's recorded prompt sequence. Two-agent coverage of the SAT domain.

**Delivered.** `cobsat` binary, 13 COBOL files with 1,347 code lines, and 9
clean git commits.

**Evidence.** DIMACS parser unit tests explicitly requested up front (empty
lines, CRLF, trailing spaces, comments between tokens). The prompt required
MiniSat/SAT4J comparison, but the partial retained record limits re-analysis
of its outcomes.

**Limitation.** Performance not profiled against MiniSat here (the sibling
does this at 8.91×), so the comparison is structural rather than
quantitative.

### `DOOM-COBOL-CLAUDE` and `DOOM-COBOL-CODEX`

**Summary.** Two real-time ray-casting games place game state and ray-casting
logic in COBOL while using narrow sidecars for terminal or graphics services.

**Delivered.** `DOOM-COBOL-CLAUDE` contains 1,616 COBOL code lines in eight
files, including seven copybooks. `DOOM-COBOL-CODEX` contains 1,906 COBOL
code lines in twelve files, including eleven copybooks. Both include scripted
replay support.

**Evidence.** Both systems build, run, render, and accept scripted input.
Source inspection confirms the intended COBOL/C boundary. A Java port belongs
to an earlier exploratory artifact and is not treated as an independent
oracle for these retained systems.

**Limitation.** The demonstrations do not provide an independent behavioral
reference or automated coverage of the full interactive state space.

### `COMPRESS-COBOL-CLAUDE` and `COMPRESS-COBOL-CODEX`

**Summary.** Two COBPACK implementations with extensive property tests.

**Delivered.** The Claude Code system contains 1,819 COBOL code lines in
three files. The Codex system contains 1,812 COBOL code lines in two files
and implements the CPC container, NONE, RLESP, and AUTO codecs, and CRC32.

**Evidence.** The replayed suite covers round trips and repeated hashes. The
Codex suite contains more than 70 assertions, including randomized round
trips, corruption checks, fuzzing, and cross-codec behavior, and its fuzzer
exposed a division-by-zero defect.

**Limitation.** The suite has no independent codec or published test vectors.
A matching encoder and decoder defect can survive a round trip, and repeated
hashes establish observed determinism rather than semantic correctness.

### `PAYROLL-COBOL-CLAUDE` and `PAYROLL-COBOL-CODEX` (six-step payroll pair)

**Summary.** Complete six-step payroll protocol (externally authored: base
program, contributions, validation and rejects, control-break report,
dual-input merge, refactoring) by both agents, with full raw logs. It
supersedes an earlier single-agent payroll attempt (steps 0–2, logs lost).

**Delivered.** `PAYROLL-COBOL-CLAUDE` (`claude-sonnet-4-6`): 535 code lines,
6 commits, 5 FDs, ERR-001..004 reject path, 12-paragraph PERFORM-only
structure. `PAYROLL-COBOL-CODEX` (`gpt-5.4`): 572 code lines, 6 commits and a
separate implementation of the same protocol.

**Evidence.** Per-step structural criteria (FD counts, rates, error codes,
paragraph names, no `GO TO`) and a post-hoc *differential execution* of the
pre- vs post-refactoring commits: payslips, rejects, report, and stdout
byte-identical for both agents.

**Limitation.** The pack's self-applied evaluation grid was not run by the
agents (author-applied structural checks instead), and
`PAYROLL-COBOL-CLAUDE` did not maintain a README/backlog (the pack's backlog
skill was not installed). Byte equality establishes preservation on the
tested inputs, not payroll-semantic correctness.

### `PYGAME-COBOL-CODEX`

**Summary.** Working cross-language interface COBOL → C → Python → pygame →
SDL.

**Delivered.** C glue, `pygame.cpy`, and example programs that run a pygame
window.

**Evidence.** An example pygame program runs and responds to input. The
agent's sandbox had no display, so this was run post hoc by the experimenter.

**Limitation.** Small API surface and no automated behavioral test suite.

### `PYGAME-COBOL-CLAUDE` (grid-completing replica)

**Summary.** Claude Code (`claude-opus-4-6`) replica of the pygame framework
from the sibling's five-step replay pack, completing the 8×2 grid. It goes
beyond the sibling's scope (BMP image support, a complete Flappy Bird).

**Delivered.** 764 COBOL code lines across 5 files (the framework copybook
and four example programs), a C SDL2 shim (`pygame_cobol.c`), a static
library, a Makefile, and a fresh-user README. In `flappy.cob`, the gravity,
the pipes, the scoring, and the game-over and restart logic are all written
in COBOL. The C shim exposes only drawing, input, and timing primitives.

**Evidence.** Clean-checkout `make` builds the framework and all four
executables (re-verified post-hoc), human-visible animation and gameplay, and
the boundary rule of the replay pack ("no C code inside the game itself")
held without experimenter intervention.

**Limitation.** Only two git commits (coarser step granularity than the
payroll pair), and no automated test harness beyond the build and
human-visible examples.

### `TTTGAME15-COBOL-CLAUDE`

**Summary.** Recursion in COBOL via `PERFORM` and explicit stack frames,
D4-symmetry-aware enumeration (255,168 games → 31,896 canonical), and base-3
minimax memoization over a 19,683-entry transposition table on the nine-cell
board.

**Delivered.** 5 executables (`game15`, `game15tree`, `game015`,
`game015tree`, `gameN`), with a 1.5% tool-output failure rate and no detected
fix cycles.

**Evidence.** Interactive verification of optimal minimax play, and an
enumeration-count cross-check (255,168 / 31,896).

**Limitation.** No automated solver-vs-human regression harness.

### `TTTGAME15-COBOL-CODEX` (cross-agent Game-of-15 replication)

**Summary.** Codex-built five-executable family mirroring the Claude Code
`TTTGAME15-COBOL-CLAUDE` and driven by the sibling's recorded prompt
sequence. Two-agent coverage of the game-of-15 / tic-tac-toe domain.

**Delivered.** 2,264 COBOL code lines across 5 files (`game15`,
`game15_tree`, `gameN.cob`, `game015.cob`, `game015tree.cob`) and 4 clean git
commits.

**Evidence.** Enumeration matches the known counts, and interactive minimax
results agree with the sibling.

**Limitation.** The sibling's recorded prompts and expected results were
available, so agreement is not an independent replication of the
game-theoretic result.

<!--
The narrative excerpts below duplicate the case descriptions and per-project
accounts. They are retained in the source for author reference but excluded
from the arXiv manuscript. (LaTeX source: wrapped in \iffalse ... \fi.)

## Appendix 7 — Per-project narratives

Each project has a short narrative summary among its secondary evidence (Core
versus secondary evidence, main paper), released alongside the study. Below we
reproduce the opening paragraph of each narrative, which states why the
project matters, together with the verbatim opening prompt that started the
collaboration. The full narratives, including chronology, validation details,
and compute context, are in the released files.

**COMPILER-COBOL-CLAUDE.** A COBOL compiler, written in COBOL, that compiles a
1,400-LOC Doom port and a 3,500-LOC chess engine. The closed loop is the point.
cobolcc.cob (≈11,000 LOC) and its sibling interpreter cobolint.cob (≈4,500
LOC) are both bootstrapped by GnuCOBOL. Once built, the resulting binary reads
COBOL source written by entirely different agent sessions and emits C that
"gcc -O2 -lm" links into native binaries. Those binaries then run: Doom renders
in a terminal, the chess engine speaks UCI, the DFS enumerations match the
GnuCOBOL reference to the last game count.
Opening prompt: "Write a COBOL compiler in COBOL. Demonstrate that you can run
some (non-trivial) COBOL programs thanks to the written compiler."

**CHESS-COBOL-CLAUDE.** On the evening of 12 March 2026 the user typed a single
paragraph into Claude Code: "I want to build a chess engine in COBOL (using GNU
Cobol)… at the end, I want to test this chess engine and assess its Elo rating,
typically by playing games against chess engines of 'similar' levels." That one
sentence kicked off a seventeen-day session that would end with a UCI-compliant
engine playing at roughly 1,630 Elo — a solid club-player level — written in a
language designed for 1960s batch payroll jobs.

**SAT-COBOL-CODEX.** A conflict-driven clause-learning SAT solver, written in
free-format COBOL, with watched literals, VSIDS, Luby restarts, first-UIP
learning, and non-chronological backjumping — finishing the SATLIB uf/uuf
benchmark sweep at 100 variables within a single-digit multiple of MiniSat's
time. That is the artefact the Codex CLI agent produced in one 14-hour session
on 2026-04-15, and it is the project worth staring at.

**DOOM-COBOL-CLAUDE / DOOM-COBOL-CODEX.** COBOL was standardised in 1960 to
process fixed-length records in batches: payroll runs, insurance ledgers,
overnight reconciliations. It has no graphics primitives, no pointers, no
real-time scheduler, no floating-point culture. "Write a Doom game in COBOL" is
therefore a category error — which is exactly why it is interesting. What
shipped from a five-word prompt is a 60 fps first-person shooter whose inner
loop — state machine, input dispatch, enemy AI, collision, pickups, level
progression — runs in COBOL paragraphs, not in the C sidecar that paints the
screen.
Opening prompt: "Write a Doom game in COBOL."

**COMPRESS-COBOL-CODEX (COBPACK).** A COBOL compressor sounds like an algorithm
exercise. The interesting thing about this project is that it refused to become
one. The project's centre of gravity sits one layer above the codec: in the
ranked feature list, the two top entries are both VER (verification) — a
48-case randomized round-trip suite and a 72-case typed-mutation fuzz suite.
The RLESP codec, the thing the project is nominally about, ranks fourth. The
fuzz suite caught a real SIGFPE in the agent's own COBOL (reclen_zero mutation
dividing by an unvalidated record length) and the fix landed in the same
session.

**CHESS-COBOL-CODEX.** A spec-first chess engine in COBOL: 184 F-### features
across 27 phases, the most disciplined backlog in the set. Architecture and
specification are authored *before* code in several phases — a professional
workflow, not vibe-coding.
Opening prompt: "I want to build a chess engine in COBOL (GNUCobol)…"

**COMPILER-COBOL-CODEX (minicobc).** The second COBOL-to-C compiler in this
study, written by Codex in one 10,535-line COBOL source file. It shares its
sibling's ambition but adds a second axis: it is measured, every step of the
way, against GnuCOBOL. GnuCOBOL is wired in as an oracle from the first
benchmark commit.
Opening prompt: "Write a COBOL compiler in COBOL. Demonstrate that you can run
some (non-trivial) COBOL programs thanks to the written compiler."

**payroll (original single-agent attempt).** An industrial-idiom payroll
program in GnuCOBOL, graded against a self-authored 27-criterion verification
grid. Textbook in the best sense: three FDs, 88-level condition names, EVALUATE
TRUE, COMPUTE ROUNDED, formatted DISPLAY. 26/28 PASS.
Opening prompt: "You are a mainframe COBOL expert. Generate a complete,
self-contained COBOL program. Domain: Payroll management system…"

**PYGAME-COBOL-CODEX.** CALL "cpg_init" USING BY VALUE width height from a
GnuCOBOL program, and an SDL2 window opens. Poll an event, blit a rectangle,
tick the clock — all via CALL into a C shim. The chain that actually runs is
COBOL → C (cpg_*) → SDL2. The agent delivered a cross-language FFI from a
language that does not have function pointers.
Opening prompt: "Write a pygame framework for COBOL (using GNUcobol)."

**TTTGAME15-COBOL-CLAUDE.** The Game of 15 is secretly tic-tac-toe (via the 3×3
magic square). Solving it in COBOL took less than 3 hours of active
collaboration. D4-symmetry canonicalization reduces 255,168 games to 31,896,
and a base-3 memoization table over the 19,683 possible boards gives optimal
play. The smoothest project in the corpus: 1.5% error rate, 0 fix cycles.

**TTTGAME15-COBOL-CODEX (Codex replica).** Byte-identical prompts, a different
agent, a substantively different architecture. The six human prompts came
verbatim from the sibling's recorded prompt sequence. The non-copy argument is
visible in the divergent file decomposition and data-structure choices.

**SAT-COBOL-CLAUDE (Claude Code replica).** The Claude Code replica of the SAT
solver, run against the exact same recorded prompt sequence that drove its
Codex sibling. Same opening prompt, same step ladder from DIMACS parser to CDCL
with watched literals. Two agents, the same replayed prompts, distinct
artifacts: the non-copy argument at its most controlled.

**COMPRESS-COBOL-CLAUDE (Claude Code replica).** When two coding agents receive
the same specification and produce different architectures, the divergence
tells you something about the agents, not the spec. The Codex sibling is a
two-file monolith; Claude Code, given the same prompt pack, chose a five-file
modular layout with a separate schema-parser subprogram. Same TRUST suite
contract, different internal structure.
-->
