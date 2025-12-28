# AI Coding Agent Instructions for Robot Sumo Tournament Project

## Project Overview
This is a competition engineering package for the All Japan Robot Sumo Tournament 2026, 500g class, targeting both Autonomous (Auto) and Remote-Controlled (RC) divisions. The project emphasizes mechanical performance, electrical reliability, and control quality under strict weight/size constraints.

## Current Phase
- **Focus**: Concept documentation and rules compliance (per `config/project.yaml`)
- **Structure**: Rules-driven development with YAML configs and Markdown docs
- **Future**: Hardware (/hardware) and software (/software) implementation

## Key Patterns
- **Configuration**: Use YAML for structured data (e.g., `config/rules_500g.yaml` for tournament constraints)
- **Documentation**: Embed inline SVGs/Mermaid diagrams in Markdown for rule visualization
- **Rules-First**: Translate tournament rules into engineering requirements (e.g., size/weight limits as design constraints)
- **Config-Driven Development**: Reference YAML configs in code and documentation for consistency

## Architecture Principles
- **Dual-Mode Design**: Support both Auto (onboard logic only) and RC (operator control) with shared hardware
- **Constraint-Driven**: All designs must comply with 500g limits (≤500g, ≤10cm width/depth at inspection)
- **Modular Components**: Separate mechanical, electrical, and software concerns

## Development Workflow
- **Validation**: Test against `config/rules_500g.yaml` specs (e.g., dohyo diameter 77cm, boundary line width 25mm)
- **Documentation**: Update README.md with implementation details as hardware/software folders are added
- **Compliance**: Reference official rulebook; avoid forbidden mechanisms (suction, projectiles, etc.)

## Code Style
- **Naming**: Use descriptive names reflecting tournament terms (e.g., `shikiri_position` for start position)
- **Comments**: Include rule references in code comments (e.g., "Per 500g rules: boundary line is 'inside'")
- **Structure**: Mirror config structure in code (e.g., constants from `rules_500g.yaml`)

## Examples
- Size checks: `if robot_width_mm > rules['rules_500g']['size_at_inspection_mm']['width']: raise ValueError("Inspection gauge violation")`
- State machine: Implement Auto start sequence (Ready → Start → Stop) per judge signals
- Config loading: `rules = yaml.safe_load(open('config/rules_500g.yaml'))`