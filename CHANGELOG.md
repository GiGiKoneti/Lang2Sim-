# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [Unreleased]

### Added
- Curated workshop issue tracks for REVA Institute open-source contributions.
- Pre-workshop environment setup documentation and verification diagnostic scripts.
- Dynamic stress-testing and obstacle perturbation modules.

---

## [v1.0.0] - Upcoming (Initial Release)

The initial major release of Lang2Sim — converting natural language into executable robot simulations with procedural world generation, zero-SLAM occupancy mapping, and closed-loop telemetry benchmarking.

### Added
- **Agentic AI Core (`lang2sim/agent/`):**
  - ReAct reasoning loop with tool-calling dispatch engine (`react_loop.py`).
  - NVIDIA Nemotron LLM integration (`nemotron_client.py`).
  - Spatial grounding pipeline converting natural language directives into spatial coordinates (`grounding.py`).
  - Strict Pydantic v2 validation contracts gating LLM input/output (`models.py`).

- **Deterministic World Synthesis & Compiler (`lang2sim/compiler/`, `lang2sim/world_gen/`):**
  - Spatial Intermediate Representation (SIR) schema generation and validation (`sir_generator.py`, `sir_validator.py`).
  - Jinja2 Gazebo Harmonic world template compiler (`world_harmonic.sdf.jinja`).
  - Shapely-backed 2D polygon clearance solver for collision-free obstacle placement (`shapely_solver.py`).
  - Zero-SLAM 2D Occupancy Map Slicer generating `.pgm` and `.yaml` costmaps analytically from 3D geometry (`map_slicer.py`).
  - Modular fixture catalog loader (`catalog_loader.py`).

- **Containerized Simulation Runtime (`lang2sim/runtime/`):**
  - Docker container runner orchestrating ROS 2 Humble + Gazebo Harmonic + Nav2 stack (`docker_runner.py`).
  - X11 and WSLg hardware-accelerated display pass-through configuration (`display.py`).
  - ROS 2 Bridge communicating with Nav2 action clients and telemetry topics (`ros_bridge.py`).
  - System health monitor, doctor diagnostics, and self-healing watchdog (`health_monitor.py`, `doctor.py`, `self_healing.py`).
  - Crash-safe run folder and recording manager (`run_folder.py`).

- **Telemetry & Trajectory Evaluation (`lang2sim/telemetry/`):**
  - Real-time ROS 2 telemetry subscribers tapping `/odom`, `/scan`, and Nav2 status (`ros_subscribers.py`, `live.py`).
  - Trajectory metric evaluator calculating Absolute Trajectory Error ($ATE$) and Relative Pose Error ($RPE$) (`trajectory.py`).
  - Navigation Quality Index ($NQI$) benchmark scorer (`nqi_scorer.py`).
  - Dockerless headless replay engine for offline evaluation and trajectory visualization (`replay.py`).

- **Terminal User Interface (`lang2sim/cli/`):**
  - Textual-powered full-screen interactive copilot dashboard (`app.py`).
  - Interactive slash commands: `/mission`, `/stress`, `/benchmark`, `/report`, `/dashboard`, `/replay`, `/help`.
  - Reactive plan cards, log streaming, and live telemetry widgets.

- **Open Source Standards & Community:**
  - Apache License 2.0.
  - Comprehensive developer guidelines in `CONTRIBUTING.md` and AI rules in `AGENTS.md`.

[Unreleased]: https://github.com/Point-Blank-Club/Lang2Sim/tree/staging
[v1.0.0]: https://github.com/Point-Blank-Club/Lang2Sim/releases/tag/v1.0.0
