# ANIMA O1

**ANIMA Open, Generation 1** — an open-source cognitive framework for home robots.

ANIMA = **A**utonomous **N**atural-language **I**nstruction **M**apping **A**rchitecture.

It turns natural-language instructions ("put the pen in the box") into grounded, executable robot behaviors by combining LLM-based parsing with classical symbolic planning and a behavior-tree runtime.

## What it is (and is not)

| | |
|---|---|
| **Is** | A reusable cognitive layer for robots running ROS 2. Parses instructions, plans tasks, dispatches skills, validates execution. |
| **Is not** | A motion planner, a perception model, a hardware driver. ANIMA *coordinates* these — it does not replace them. |

ANIMA is the brain shared across the **Soma Homies** robot family ([SmartRobotArm](https://github.com/jeffliulab/SmartRobotArm) is the first robot using it — a fixed tabletop manipulator that will become the arm capability layer of the future Soma Home), but it is designed to be robot-agnostic.

**Why ANIMA exists.** The goal of building the ANIMA cognitive framework is to eventually realize the SOMA home robot — a household robot that helps with chores and makes everyday life happier.

## Status

**Pre-alpha.** This is the v1 (`O1`) open-source line — the first generation we are willing to put under public version control. Expect frequent breaking changes until we cut a `0.1.0` tag.

Design docs (Chinese, more abstract) live in [`SOMA/ANIMA_FRAMEWORK/`](https://github.com/jeffliulab/SOMA) — that's where ideas are sketched before they land here.

## Architecture (planned)

```
       natural language instruction
                  │
                  ▼
        ┌─────────────────┐
        │  LLM Parser     │  instruction → TaskSpec (structured)
        └────────┬────────┘
                 │
                 ▼
        ┌─────────────────┐
        │  Task Planner   │  TaskSpec → BehaviorTree
        └────────┬────────┘
                 │
                 ▼
        ┌─────────────────┐
        │  Skill Registry │  selects + dispatches primitive skills
        └────────┬────────┘
                 │
                 ▼
        ┌─────────────────┐
        │  Skill Executor │  ROS 2 actions / services to robot
        └────────┬────────┘
                 │
                 ▼
        ┌─────────────────┐
        │  Validator      │  test-and-check before reporting success
        └─────────────────┘
```

Core design principle: **LLM-as-a-Parser, not LLM-as-a-Translator.** The LLM produces structured task representations that downstream symbolic components can verify, instead of generating low-level commands directly.

## Repository layout

```
ANIMA_O1/
├── README.md
├── LICENSE                  # (TBD)
├── pyproject.toml           # (TBD)
└── src/
    └── anima/
        └── __init__.py      # version + public API surface
```

More structure will be added as the framework grows. See the design docs for the planned full layout.

## License

[Apache License 2.0](LICENSE) — Copyright 2026 Jeff Liu Lab ([jeffliulab.com](https://jeffliulab.com), GitHub [@jeffliulab](https://github.com/jeffliulab)).

You may use, modify, and redistribute this code commercially or privately, provided you keep the copyright and license notices and document any changes you make. Contributors grant an explicit patent license; suing a contributor over patents in this work terminates your license.
