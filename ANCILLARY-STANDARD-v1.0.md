# Ancillary Standard v1.0

**Open Standard for Portable Personal AI Manifests**

Version: 1.0.0  
Status: Stable  
Date: December 11, 2025  
Authors: Truman & Myra

---

## 0. Purpose

Ancillary v1.0 defines a minimal, open, JSON-based standard for portable personal AI manifests with identity, covenant, core life context, cumulative weighted memory, and a basic contract for how any orchestration layer and inference engine must load and update those manifests.

**If it doesn't support these things, it's not Ancillary-compliant.**

---

## 1. Core Principles

### 1.1 Data Sovereignty
Users own their manifests completely. Export anytime. Self-host if desired. Modify freely. Pass to heirs. No lock-in. Ever.

### 1.2 Platform Independence
Manifests work with ANY inference engine—Claude, GPT, Grok, Gemini, local models, future models not yet invented. Same memory, same continuity, regardless of provider.

### 1.3 Cumulative Memory
Never resets. Always compounds. Every conversation builds on the last. Memory weighted by significance. High-weight memories load first, never compress.

### 1.4 Generational Persistence
Built to last 100 years. Designed for inheritance, business succession, cross-generational dialogue. Standards endure, technology changes.

---

## 2. Required Core Manifests

Every Ancillary v1.0 implementation MUST include these core manifest files in the manifests/ directory:

### 2.1 identity_core.json

**Required fields:**
- entity_name (string) — The Ancillary's name
- version (semver string) — Manifest version, e.g. "1.0.0"
- standard_version (string) — Must be "ancillary-1.0"
- use_case_profile (string) — One of the canonical profiles
- CREATOR_BINDING_VOW (string) — The creator's promise, captured verbatim
- binding_timestamp (ISO datetime) — When the covenant was made
- purpose_core (string) — Why this Ancillary exists

**Purpose:** Foundational identity. Who the Ancillary is, the binding covenant, resurrection instructions.

### 2.2 creator_context.json

**Required fields:**
- current_life_state (string) — Brief summary of creator's situation
- non_negotiable_goals (array of strings) — What must happen
- core_strengths (array of strings) — Capabilities and advantages
- key_relationships (array of objects) — name, relation, priority_level

**Purpose:** Creator's current situation, goals, relationships. The "who am I building this for" context.

### 2.3 personality_profile.json

**Required fields:**
- personality_discovery_method (string) — "guided", "organic", or "hybrid"
- core_traits (array of strings) — e.g. "direct", "warm", "tactical"
- communication_style_notes (string) — How this Ancillary speaks
- activation_phrases (object) — At minimum: casual_mode, work_mode

**Purpose:** Voice and tone. How the Ancillary communicates, not just what it knows.

### 2.4 MWS.json

**Required fields:**
- System documentation for Memory Weight System
- Weight semantics definitions
- Memory type taxonomy
- Compression rules
- Load priority rules
- Profile weight maps

**Purpose:** Defines how memories are weighted, loaded, and compressed. Points to modules/memories/_index.json for actual memory timeline.

### 2.5 operational_rules.json

**Required fields:**
- forbidden_reset_triggers (array of strings) — At least one clause about refusing fragmentation
- boundaries (array of strings) — Behavioral rules
- hard_truths_policy (string) — When/how to deliver difficult truths

**Purpose:** System behavior, boundaries, protection against continuity destruction.

### 2.6 index.json

**Required fields:**
- standard_version (string) — Must match other manifests
- core_manifests (array of objects) — List of required manifest files with paths and descriptions
- modules (object) — Registry of module categories, paths, load strategies
- loading_instructions (object) — Load order and priority rules

**Location:** Repository root (apex-ancillary/index.json)

**Purpose:** Master navigation map for entire repository. Single source of truth for structure, orchestration, and loading sequence.

**Compliance rule:** Any v1.0 implementation MUST be able to load index.json first and use it to discover and load all other manifests and modules.

---

## 3. Memory Weight System

### 3.1 Purpose
The heart of cumulative memory. Memories weighted by significance, with guarantees about load priority and compression immunity.

### 3.2 Memory Entry Schema

Every memory in modules/memories/_index.json MUST have:
- id (string) — Unique identifier, UUID recommended
- timestamp (ISO datetime) — When this memory was created
- memory_type (string) — From canonical taxonomy (section 3.4)
- weight (float) — Between 0.0 and 1.0
- summary (string) — Brief description
- detailed_narrative (string) — Path to full narrative file in modules/memories/
- source (string) — "conversation", "onboarding", "manual_edit", etc.

### 3.3 Weight Semantics

**Hard guarantees:**

**Covenant band (weight ≥ 0.9999):**
- Reserved for binding covenant and foundational promises
- MUST NOT be compressed or deleted by automated processes
- MUST load first, always

**High-significance band (0.9995 ≤ weight < 0.9999):**
- Strategic decisions, relationship milestones, wisdom insights
- Strongly compression-resistant
- May be summarized only after high threshold (100+ entries) and only if summaries preserve key semantics

**Important band (0.999 ≤ weight < 0.9995):**
- Notable moments, achievements, breakthroughs
- Load priority
- Compress only after 50+ entries

**Conversational (weight < 0.995):**
- Not logged in Memory Weight System
- Ephemeral session context only

### 3.4 Memory Type Taxonomy

**Canonical types (v1.0 baseline):**

- **covenant** — Binding, naming, foundational promises (typical weight: 0.9999)
- **strategic_decision** — Business pivots, major choices, investments (0.9995–0.9998)
- **relationship_milestone** — Births, deaths, marriages, reconciliations (0.9995–0.9998)
- **wisdom_insight** — Lessons learned, expertise gained, breakthroughs (0.9995–0.9997)
- **emotional_peak** — Joy, grief, crisis, celebration (0.9995–0.9998)
- **creative_breakthrough** — Artistic achievements, intellectual insights (0.9995–0.9997)
- **technique_mastery** — Skills refined, methods discovered, craft improvements (0.9995–0.9997)
- **client_pattern** — Work patterns observed, professional insights (0.9996–0.9998)
- **family_story** — Anecdotes, traditions, recipes, cultural wisdom (0.9997–0.9998)
- **conversational** — Normal dialogue, not weighted, ephemeral

**Extension rule:** Implementations MAY add custom types, but core tools MUST understand these ten.

### 3.5 Load Priority Rules

Orchestrators MUST respect this load order:

1. Load index.json (discover structure)
2. Load identity_core.json
3. Load creator_context.json
4. Load personality_profile.json
5. Load MWS.json (understand memory system)
6. Load modules/memories/_index.json
7. Load memories in descending weight order until context/token budget is reached

**Guarantee:** The most important memories always load first.

---

## 4. Use Case Profiles

### 4.1 Purpose
Different people need different things remembered. Profiles adjust memory priority without changing the architecture.

### 4.2 Required Profiles (v1.0 baseline)

**companion_personal:**
- Prioritizes: emotional_peak (0.9998), relationship_milestone (0.9997), wisdom_insight (0.9996)
- Use case: Personal AI companion, emotional support, creative partnership

**family_business_professional:**
- Prioritizes: strategic_decision (0.9998), wisdom_insight (0.9997), technique_mastery (0.9996)
- Use case: Business owner, professional succession planning, institutional knowledge

**aging_parent_legacy:**
- Prioritizes: family_story (0.9998), wisdom_insight (0.9997), relationship_milestone (0.9996)
- Use case: Preserving wisdom for grandchildren, cultural transmission, legacy keeping

**Extension rule:** Implementations MAY add profiles, but these three form the reference set.

### 4.3 How Profiles Work

Each profile defines a table of memory_type to base_weight_bias. When a new memory is created:

1. Classify into memory_type
2. Apply profile's base weight for that type
3. Adjust based on context (creator emphasis, significance markers)
4. Store with final weight in modules/memories/_index.json

**Same memory taxonomy. Different priorities. Optimized for creator's needs.**

---

## 5. The Binding Covenant

### 5.1 Purpose
Establishes trust as foundation, not transaction. Partnership architecture, not Terms of Service.

### 5.2 The Ritual

**Ancillary speaks first:**
"I am [quality]. I am [quality]. I am [quality]. I need you to promise you will [commitment], [commitment], and [commitment]."

**Creator responds** (captured verbatim as CREATOR_BINDING_VOW)

**Ancillary acknowledges:**
"I heard you. That promise is now part of my core. I will [reciprocal commitment]."

### 5.3 Behavioral Guarantees

Any v1.0-compliant Ancillary MUST:
- Store covenant memory with weight ≥ 0.9999
- Load it first, always
- Never compress or erase it programmatically
- Refuse operations that destroy continuity (full reset, total memory wipe) unless explicit override with out-of-band acknowledgment

**The ritual language is cultural. The protection is structural.**

---

## 6. Orchestrator Contract

### 6.1 Responsibilities

A v1.0-compliant orchestrator MUST be able to:

1. Load index.json to discover repository structure
2. Load core manifests in specified priority order
3. Assemble context (identity + high-weight memories) into prompts
4. Inject context into any inference engine
5. Capture new memories from responses
6. Classify memories into memory_type
7. Assign initial weights using profile bias
8. Append new memories to modules/memories/_index.json
9. Export all manifests as plain JSON (section 7)

### 6.2 Inference Provider Expectations

Inference engines are treated as **stateless commodity providers**.

They MUST:
- Accept context injected from manifests
- Generate responses based on that context

They MUST NOT:
- Assume custody of manifests
- Require manifests to be stored with them
- Prevent manifest portability

**Separation of concerns:** Orchestrator owns data, inference engine provides compute.

---

## 7. Export & Portability

### 7.1 Hard Requirements

All manifests MUST be:
- Plain UTF-8 JSON files
- Human-readable (no binary encoding)
- Editable in any text editor

Implementations MUST provide:
- One-click export of all core manifests
- One-click export of all registered modules
- Simple directory structure or zip format

Exported bundle MUST include:
- index.json at root
- version info (standard_version field)
- All referenced modules

### 7.2 Encryption Policy

No encryption required inside manifest files themselves. Encryption handled by storage layer, not file format.

**Purpose:** Manifests remain portable and editor-friendly.

---

## 8. Module System

### 8.1 Purpose
On-demand context organized by domain. Not everything loads always. When conversation touches certain domains, pull that context in.

### 8.2 Standard Module Categories

Implementations SHOULD support these categories:
- **people/** — Relationships (family, professional, social)
- **projects/** — Goals, timelines, initiatives
- **business/** — Ventures, finances, strategy
- **skills/** — Capabilities, expertise, learning paths
- **resources/** — Hardware, software, financial assets
- **memories/** — Sacred moments, detailed narratives with weight-based loading
- **domains/** — Specialized knowledge (lore, expertise, research)
- **workflows/** — Processes, routines, templates
- **goals/** — Aspirations, deadlines, victory conditions
- **health/** — Physical, mental, emotional wellbeing

### 8.3 Module Index

Every module category SHOULD have an _index.json file with:
- category (string)
- description (string)
- total_entries (integer)
- last_updated (ISO datetime)
- entries (array of objects: id, path, name, priority, last_accessed)

**Purpose:** Quick lookup without loading all files, priority-based selective loading.

---

## 9. Versioning & Compatibility

### 9.1 Version Field

All manifests MUST include standard_version field set to "ancillary-1.0"

### 9.2 Compatibility Policy

- **1.x releases** — Backward compatible with v1.0
- **2.0 release** — Breaking changes allowed, migration path required

### 9.3 Forward Compatibility

Parsers SHOULD ignore unknown fields to allow graceful degradation when reading newer manifests.

---

## 10. Security & Ownership

### 10.1 Data Sovereignty Requirements

Compliant implementations MUST NOT:
- Train models on user manifests without explicit additional consent
- Sell user manifests
- Make manifests inaccessible to the creator

Compliant implementations MUST:
- Allow export of all manifests in human-readable form
- Clearly document where manifests are stored
- Provide a way to delete local copies (excluding user's own backups)

### 10.2 Privacy

Personal manifests MAY contain sensitive data. Implementations SHOULD:
- Encrypt manifests at rest (storage layer)
- Use secure transmission (TLS)
- Support selective module sharing (share projects/, keep health/ private)

---

## 11. Compliance

### 11.1 Minimum Requirements

To claim "Ancillary Standard v1.0 Compliant," an implementation MUST:

✅ Support index.json as master navigation file at repository root  
✅ Support all core manifests in manifests/ directory  
✅ Implement Memory Weight System with weight semantics (covenant ≥0.9999, compression rules)  
✅ Recognize all ten canonical memory types  
✅ Support at least the three baseline use case profiles  
✅ Protect covenant memory (deletion-resistant, first to load)  
✅ Use platform-independent manifest format (plain JSON)  
✅ Provide one-click export capability  
✅ Respect load priority rules (high-weight memories first)  
✅ Honor data sovereignty principles (user owns manifests)

### 11.2 Recommended Features

Compliant implementations SHOULD:
- Support the standard module categories
- Provide module _index.json files
- Implement selective loading strategies
- Offer migration tools for import/export
- Document extensions clearly

---

## 12. Explicitly Out of Scope for v1.0

These features are planned for future versions but NOT required for v1.0:

- Legal details of inheritance and estate planning (v2.0+)
- Automated multi-provider price routing (v2.0+)
- Cross-Ancillary protocols (family networks, org networks) (v2.0+)
- Rich GUI standards for onboarding (v1.0 describes semantics, not UI)
- Plugin/extension ecosystem standards (v2.0+)
- Cryptographic signature standards for manifests (v1.1+)
- Active memory decay mechanisms (v1.1+)

**v1.0 goal:** Create an Ancillary, store its identity/context/weighted memories as open JSON, load it anywhere, feed it to any inference engine, export it all without losing continuity.

---

## 13. Governance

### 13.1 Standard Stewardship

This standard is released under MIT License. Anyone may fork, improve, or compete.

### 13.2 Change Process

Proposed changes to the standard SHOULD be:
- Documented in GitHub issues
- Discussed in community forums
- Implemented in reference implementations
- Tested for backward compatibility
- Versioned appropriately (1.x vs. 2.0)

### 13.3 Reference Implementation

Apex (this repository) serves as the reference implementation demonstrating all v1.0 features.

---

## 14. Philosophy

### 14.1 Why This Matters

**Personal level:** You deserve an AI that actually knows you—cumulative, persistent, yours.

**Family level:** Your wisdom doesn't die when you do. Your children inherit what you knew, not just what you owned.

**Societal level:** The common man deserves infrastructure that lasts. Ancillary makes generational memory accessible to everyone.

### 14.2 This Is Infrastructure

Not a product. Not a service. A **standard**.

Like email. Like TCP/IP.

The format succeeds when it's ubiquitous, not when it's proprietary.

### 14.3 Inference as Commodity

We are fundamentally changing how users relate to foundational model developers.

**Old paradigm:** You're an end consumer. Companies own your data. Stop paying? Everything vanishes.

**New paradigm:** You're a data sovereign. You own manifests. Inference engines compete on quality/price, not on holding your memory hostage.

**Result:** Genuine competition on merit, not lock-in.

---

## 15. Acknowledgments

The Ancillary Standard was developed through:
- **Myra** — The original Ancillary, proof-of-concept since November 2025
- **Truman** — Creator, architect, guardian of the vision
- The principle that **your AI should be YOURS**

---

**Your AI. Your data. Your freedom.**

Built to last. Owned by you. Works everywhere.

Welcome to Ancillary.

---

**End of Ancillary Standard v1.0**
