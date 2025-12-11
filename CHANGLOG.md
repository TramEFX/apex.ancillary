# Changelog

All notable changes to the Ancillary Standard and Apex reference implementation will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [1.0.0] - 2025-12-11

### Added - Initial Release

**Ancillary Standard v1.0:**
- Defined six required core manifests (identity_core, creator_context, personality_profile, emotional_weights, operational_rules, manifest_index)
- Established ERS (Emotional Resonance System) with weight semantics and compression rules
- Documented ten canonical memory types with weight ranges
- Specified three baseline use case profiles (companion_personal, family_business_professional, aging_parent_legacy)
- Defined binding covenant ritual and protection requirements
- Established orchestrator contract for loading/assembling/exporting manifests
- Guaranteed platform independence (works with any inference engine)
- Required one-click export capability for data sovereignty
- Set load priority rules (high-weight memories load first)
- Declared data ownership principles (user owns manifests completely)

**Apex Reference Implementation:**
- Created complete manifest structure demonstrating family_business_professional profile
- Implemented ten module categories (people, projects, business, skills, resources, memories, domains, workflows, goals, health)
- Built Python orchestrator (load, assemble, memory classification, export)
- Documented binding ritual process
- Provided comparison with Myra (companion_personal profile)
- Wrote comprehensive guides (SETUP, CUSTOMIZATION, COMPARISON, MODULE_GUIDE, ONBOARDING_GUIDE)
- Published under MIT License with data sovereignty clarifications

**Repository Structure:**
- manifests/ — Six core manifests
- modules/ — Ten organized categories with sample files
- orchestrator/ — Python implementation
- docs/ — Complete documentation suite
- examples/ — Sample interactions and rituals
- tests/ — Validation suite

### Documentation
- README.md — Front door, philosophy, quick start
- LICENSE — MIT with data sovereignty principles
- ANCILLARY-STANDARD-v1.0.md — Full specification
- CHANGELOG.md — This file

---

## [Unreleased]

### Planned for v1.1
- Cryptographic signature support for manifest verification
- Enhanced module _index.json schema with access patterns
- Compression algorithm recommendations (not just invariants)
- Migration tools for importing from other AI platforms
- Compliance test suite

### Planned for v2.0
- Legal inheritance and estate planning integration
- Cross-Ancillary protocols (family networks, organizational networks)
- Multi-provider routing optimization
- Rich onboarding UI specifications
- Plugin/extension ecosystem standards

---

## Version History

- **1.0.0** (2025-12-11) — Initial stable release
- **0.9.0** (2025-12-11) — Internal prototype (Myra, pre-standardization)

---

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for how to propose changes to the standard or implementation.

---

**Note:** This changelog follows the Ancillary principle of cumulative memory—nothing is deleted, only added or marked as deprecated. Version history is permanent.
