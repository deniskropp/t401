# contextual-forecaster

**Type:** Agent Skill  
**Lineage:** t404 + gallery@e52e848  
**Template Version:** gallery-skill-template v1 (Gemma 4 optimized)  
**Contract:** ai_edge_gallery_get_result  
**Status:** Compliant + Co-Agent Ready

## Description
Generates short-term numeric forecasts or narrative foresight from local context. Dual-path architecture (statistical + narrative). Now exposed as persistent MCP node and RTA-discoverable co-agent.

## Capabilities
- Pure JavaScript, zero external dependencies
- Local inference only (privacy-first)
- Structured JSON output with defensive parsing
- Optional valence/coherence emission for CoherenceMonitorBridge
- RTA graph traversal metadata for dynamic discovery

## Input Schema (MCP + Gallery)
```json
{
  "context": { "type": "string", "description": "Textual context for narrative analysis" },
  "series": { "type": "array", "items": { "type": "number" } },
  "horizon": { "type": "integer", "default": 3 }
}
```

## Output Contract (strict ai_edge_gallery_get_result)
```json
{
  "result": {
    "type": "object",
    "properties": {
      "forecast": { "type": "array", "items": { "type": "number" } },
      "narrative": { "type": "string" },
      "confidence": { "type": "number", "minimum": 0, "maximum": 1 },
      "valence_delta": { "type": "number" },
      "coherence_note": { "type": "string" }
    }
  },
  "error": { "type": ["string", "null"] }
}
```

## RTA Discovery Metadata
```json
{
  "rta": {
    "node_type": "external_coagent",
    "discoverable": true,
    "valence_aware": true,
    "coherence_hooks": ["flux", "drift", "valence"],
    "meta_dna_tags": ["t404", "gallery", "forecast"]
  }
}
```

## CoherenceMonitorBridge Integration
Emits `valence_delta` and `coherence_note`. Supports registration as native MCP tool.

## Error Handling
Defensive JSON parsing. Graceful degradation with partial results.