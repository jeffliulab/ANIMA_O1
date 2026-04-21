# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.1.0] - 2026-04-21

### Added
- First reference implementation absorbed from the `anima-intention-action` BCI application branch.
- Six-layer stack with working code:
  - L0 Signal (`l0_signal.py`) — upstream signal interface (BCI / speech / vision / text).
  - L1 Parser (`l1_parser.py`) — LLM-as-Parser with forced tool-calling (`LLMToolCaller` protocol, provider-agnostic).
  - L2 Planner (`l2_planner.py`) — TaskSpec → `py_trees` BehaviorTree.
  - L3 Skill (`l3_skill.py`) — `MockSkillBehaviour` + abstract `SkillBehaviour` base class.
  - L4 Adapter (`l4_adapter.py`) — `EmbodiedAdapter` protocol + `MockAdapter` for offline tests.
  - L5 Assessment (`l5_assessment.py`) — ITA / MQA / SQA / GOA / PEA with concrete formulas.
- Test-and-Check gates (`test_and_check.py`) — intent / skill / params / safety validation.
- TaskSpec Pydantic v2 schemas (`taskspec.py`).
- `pyproject.toml`, pip-installable via `pip install -e .`.
- Unit tests (`tests/test_pipeline.py`) — end-to-end smoke tests for L0 waveform, gates, behavior tree, five-factor.
- Open-source governance: `CONTRIBUTING.md`, `SECURITY.md`, `CODE_OF_CONDUCT.md`.
- Preserved original IP documents under `docs/preserved/` (framework design, ALICE inspirations, public README).

### Changed
- Package renamed from `anima_intention_action` → `anima`.
- `l0_neural.py` renamed to `l0_signal.py`; `NeuralDecoder` protocol renamed to `SignalDecoder`. The layer still carries BCI drift metadata but is now explicitly documented as domain-agnostic (speech, vision, text inputs are also L0 sources).
- `README.md` rewritten: framework is now explicitly domain-agnostic; BCI-medical is one application branch (`soma-care`), not the definition. Tabletop manipulation (`soma-arm`) is the second reference application.
- Version jumped from `0.0.0` (skeleton) to `0.1.0` (first working implementation).

### Notes
- The framework is alpha; APIs may still change prior to `1.0.0`.
- BCI-specific documentation (`docs/bci-adaptation/`) and medical-compliance material have been moved downstream to `soma-care`, where they belong with the application.

## [0.0.0] - 2026-04-16

### Added
- Initial skeleton: package layout, license, README describing the intended architecture.

## Template

```
## [x.y.z] - YYYY-MM-DD

### Added
- ...

### Changed
- ...

### Deprecated
- ...

### Removed
- ...

### Fixed
- ...

### Security
- ...
```
