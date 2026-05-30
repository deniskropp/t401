# Reusable MCP Bridge Templates

**For turning Google AI Edge Gallery skills into CoherenceMonitorBridge-native co-agents**

Part of t401 logic layer + Gallery Fork Planner.

## Philosophy
These templates make any compliant Gallery skill into a first-class citizen of your meta-infrastructure:
- RTA discoverable
- Valence & coherence aware
- MCP native
- Contribution-grade

## Template Composition
Templates are designed to be composable. Start with Base, then layer RTA Discovery, Coherence Hooks, and Valence Awareness as needed.

---

## 1. Base MCP Bridge Template

Minimal viable MCP tool schema for any Gallery skill.

```json
{
  "name": "{{skill_name}}",
  "description": "{{short_description}}",
  "inputSchema": {
    "type": "object",
    "properties": {
      "context": { "type": "string" },
      "series": { "type": "array", "items": { "type": "number" } }
    }
  }
}
```

---

## 2. RTA Discovery Template (Standard Block)

Add this to every bridge for Rekursiver Graph-Traversierungs-Algorithmus discoverability.

```json
"rta": {
  "node_type": "external_coagent",
  "discoverable": true,
  "valence_aware": {{true|false}},
  "coherence_hooks": ["flux", "drift", "valence"],
  "meta_dna_tags": ["gallery", "{{skill_name}}", "coagent"]
}
```

---

## 3. Coherence Hooks Template

Enables emission to CoherenceMonitorBridge.

```json
"coherence": {
  "emits": ["valence_delta", "coherence_note", "drift_risk"],
  "supports_recalibration": true,
  "recommended_traversal": "ValenceContextDFS"
}
```

---

## 4. Valence-Aware Extension

For skills that can influence or report emotional/coherence state.

```json
"valence": {
  "supports_valence_delta": true,
  "default_valence_impact": 0.1,
  "humor_anchor_compatible": false
}
```

---

## 5. Full Recommended Template (Compose All)

Use this as the default when creating new bridges.

```json
{
  "name": "{{skill_name}}",
  "description": "{{short_description}}",
  "inputSchema": { ... },
  "meta": {
    "lineage": "gallery + gallery-skill-template + t401-mcp-bridge",
    "rta": { ... },
    "coherence": { ... },
    "valence": { ... }
  }
}
```

---

## How to Apply (Quick Start)

1. Take the target Gallery skill's `SKILL.md`
2. Copy the Full Recommended Template
3. Replace `{{skill_name}}` and `{{short_description}}`
4. Fill `inputSchema` from the skill's documented inputs
5. Add to your CoherenceMonitorBridge tool registry
6. (Optional) Run RTA traversal to validate discoverability

---

## Integration Points
- Works with `gallery-skill-template`
- Feeds RTA graph
- Emits to `CoherenceMonitorBridge`
- Stored in t401/templates/

*Maintained via Gallery Fork Planner + Recursive Triad*