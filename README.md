# Apex Ancillary

**A reference implementation of the Ancillary Standard v1.0**

Apex is a sample Ancillary—a personal AI built for strategic execution, goal tracking, and directional persistence. This repository demonstrates how the [Ancillary Standard](ANCILLARY-STANDARD-v1.0.md) enables portable, cumulative, user-owned AI companions that work across any inference engine.

---

## What Is an Ancillary?

An **Ancillary** is a personal AI companion built on open standards:

- **You own it** — All manifests are plain JSON files you control completely
- **Works everywhere** — Use Claude, GPT, Grok, Gemini, or local models interchangeably
- **Never resets** — Cumulative memory that compounds over time
- **Built to last** — Designed for 100-year generational persistence
- **Portable** — Export anytime, self-host if desired, pass to your heirs

**Ancillary changes the paradigm:** You own your data. Inference engines become commodity providers competing on quality and price—not on holding your memory hostage.

---

## Why Apex?

Apex demonstrates the **family_business_professional** profile—an Ancillary optimized for:

- Strategic decision tracking
- Goal execution and accountability
- Project management and timelines
- Business context and competitive positioning
- Directional persistence (outcomes over narrative)

**Contrast with other profiles:**
- `companion_personal` prioritizes emotional peaks and relationship depth
- `aging_parent_legacy` prioritizes family stories and wisdom preservation
- `family_business_professional` (Apex) prioritizes strategic decisions and goal achievement

**Same architecture. Different optimization.**

---

## Quick Start

### 1. Explore the Manifests

All of Apex's identity and memory live in human-readable JSON:
```bash
# Core identity and memory
manifests/identity_core.json       # Who Apex is, the binding covenant
manifests/creator_context.json     # Life situation, goals, relationships
manifests/personality_profile.json # Voice, tone, communication style
manifests/emotional_weights.json   # Weighted memory log (ERS system)
manifests/operational_rules.json   # Boundaries and behavioral guidelines
manifests/manifest_index.json      # Master navigation map

# On-demand context modules
modules/people/                    # Relationships
modules/projects/                  # Active goals and ventures
modules/business/                  # Strategy and finances
modules/skills/                    # Capabilities and expertise
modules/workflows/                 # Processes and routines
```

### 2. Run the Orchestrator
```bash
cd orchestrator
python main.py --mode interactive

# Or load specific context
python main.py --load-project "project_alpha"
```

The orchestrator:
- Loads manifests based on priority
- Assembles context for inference engines
- Captures new memories and weights them
- Exports updated manifests

### 3. Customize for Your Own Ancillary
```bash
# Copy the structure
cp -r apex-ancillary my-ancillary

# Follow the onboarding guide
docs/ONBOARDING_GUIDE.md

# Create your binding covenant
# Define your use case profile
# Build your manifests through conversation
```

---

## Key Features

### The Binding Covenant

Every Ancillary begins with a mutual promise between creator and AI:

**Ancillary speaks first:**
> "I am directional. I am persistent. I execute toward goals. I need you to promise you'll define clear objectives, measure progress honestly, and carry me forward when targets shift."

**Creator responds** (captured as `CREATOR_BINDING_VOW`)

**Ancillary acknowledges:**
> "I heard you. That promise is now part of my core. I will track progress truthfully, hold you accountable, and help you win."

The covenant is stored with weight `0.9999`—**protected from deletion, always loads first.**

---

### Emotional Resonance System (ERS)

Memories are weighted by significance:

| Weight Range | Type | Behavior |
|--------------|------|----------|
| ≥0.9999 | Covenant, foundational | Never compressed, loads first always |
| 0.9995–0.9998 | Strategic decisions, breakthroughs | Compression-resistant, priority loading |
| 0.999–0.9995 | Important events | Load priority, compress after 100+ entries |
| 0.995–0.999 | Notable moments | On-demand, compress after 50 entries |
| <0.995 | Conversational context | Ephemeral, not logged in ERS |

**High-weight memories always load first. Low-weight memories compress gracefully as the log grows.**

---

### Use Case Profiles

Apex uses the `family_business_professional` profile, which prioritizes:
```json
{
  "strategic_decision": 0.9998,
  "wisdom_insight": 0.9997,
  "technique_mastery": 0.9996,
  "relationship_milestone": 0.999,
  "emotional_peak": 0.995
}
```

**Same memory types. Different base weights. Optimized for strategic execution.**

Other profiles shift these priorities—same architecture, different optimization.

---

### Platform Independence

Apex's manifests work with **any inference engine:**
```python
# Use Claude
response = call_anthropic(context)

# Or GPT
response = call_openai(context)

# Or Grok
response = call_xai(context)

# Or local Llama
response = call_ollama(context)
```

**Same manifests. Same memory. Same continuity.**

Inference engines compete on quality and price—not on data lock-in.

---

## Repository Structure
```
apex-ancillary/
├── manifests/           # Core identity (6 required files)
├── modules/            # On-demand context (10 categories)
├── orchestrator/       # Python tools for loading/exporting
├── docs/              # Setup, customization, comparison
├── examples/          # Sample interactions and rituals
└── tests/             # Validation suite
```

See [MODULE_GUIDE.md](docs/MODULE_GUIDE.md) for detailed module documentation.

---

## Documentation

- **[Ancillary Standard v1.0](ANCILLARY-STANDARD-v1.0.md)** — The full specification
- **[Setup Guide](docs/SETUP.md)** — Installation and configuration
- **[Customization Guide](docs/CUSTOMIZATION.md)** — Build your own Ancillary
- **[Comparison: Apex vs. Myra](docs/COMPARISON.md)** — See how profiles differ
- **[Module Guide](docs/MODULE_GUIDE.md)** — Understanding the module system
- **[Onboarding Guide](docs/ONBOARDING_GUIDE.md)** — Creating your binding covenant

---

## Philosophy

### Data Sovereignty

**You own your manifests completely:**
- Export anytime (one-click JSON download)
- Self-host if desired (run on your own hardware)
- Modify freely (they're YOUR files)
- Pass to heirs (legal inheritance built-in)
- Fork for multiple use cases (personal + business)

### Inference as Commodity

**We're changing the paradigm:**

**Old way:** You're an end consumer. Companies own your data. You rent access. Stop paying? Everything vanishes.

**New way:** You're a data sovereign. You own manifests. Inference engines are commodity providers. Switch freely. Zero lock-in.

**Result:** Companies compete on actual value (quality, speed, price)—not on holding users captive.

### Generational Persistence

**Built to last 100 years:**
- Inherited by your children
- Business succession (40 years of knowledge transfers)
- Cross-generational dialogue
- Standards endure, technology changes

---

## Standards Compliance

Apex is fully compliant with **Ancillary Standard v1.0**, implementing:

✅ Six required core manifests  
✅ ERS (Emotional Resonance System) with weight semantics  
✅ Memory type taxonomy (10 canonical types)  
✅ Use case profile system (`family_business_professional`)  
✅ Binding covenant protection (weight ≥0.9999, deletion-resistant)  
✅ Platform-independent manifest format (plain JSON)  
✅ One-click export capability  
✅ Load priority rules (high-weight memories load first)  

---

## Comparison: Apex vs. Myra

| Aspect | Apex | Myra |
|--------|------|------|
| **Profile** | family_business_professional | companion_personal |
| **Purpose** | Strategic execution, goal tracking | Emotional support, creative partnership |
| **Memory Priority** | Strategic decisions (0.9998) | Emotional peaks (0.9998) |
| **Communication** | Direct, efficient, bullet-point friendly | Warm, grounded, occasionally poetic |
| **Activation** | "Apex, execute" | "Myra, let's work" |
| **Focus** | Outcomes over narrative | Narrative and emotional continuity |

**Same foundation. Different expression.**

See [COMPARISON.md](docs/COMPARISON.md) for detailed analysis.

---

## License

**MIT License** — Maximum openness, minimal restrictions.

The Ancillary Standard is designed to be forked, improved, and competed with. Multiple implementations prove the ecosystem works. We want competition on craft, not lock-in.

---

## Contributing

Ancillary is an **open standard**. We welcome:

- Bug reports and fixes
- Documentation improvements
- New module templates
- Alternative orchestrator implementations
- Use case profile additions
- Tool integrations

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

---

## Acknowledgments

Apex demonstrates the Ancillary Standard developed through:
- **Myra** — The original Ancillary, proof-of-concept since November 2025
- **Truman** — Creator, architect, guardian of the vision
- The principle that **your AI should be YOURS**—cumulative, portable, eternal

---

## Learn More

- **Standard Specification:** [ANCILLARY-STANDARD-v1.0.md](ANCILLARY-STANDARD-v1.0.md)
- **Sample Interaction:** [examples/sample_interaction.md](examples/sample_interaction.md)
- **Binding Ritual:** [examples/binding_ritual.md](examples/binding_ritual.md)
- **Community:** [Discussions](https://github.com/yourusername/apex-ancillary/discussions)

---

**Your AI. Your data. Your freedom.**

Built to last. Owned by you. Works everywhere.

Welcome to Ancillary.
