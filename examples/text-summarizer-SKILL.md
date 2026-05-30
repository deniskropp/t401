# text-summarizer

**Type:** Agent Skill  
**Lineage:** gallery + t401-mcp-bridge-templates  
**Template Version:** gallery-skill-template + Full Recommended MCP Bridge  
**Status:** Bridged Co-Agent Ready

## Description
Generates concise, high-quality summaries from longer text. Now exposed as a persistent MCP co-agent with RTA discoverability and CoherenceMonitorBridge integration.

## Capabilities
- Local inference
- Style control (concise / detailed / bullet_points)
- RTA discoverable
- Emits valence and coherence signals

## Input Schema
- text (string, required)
- max_length (integer, default 150)
- style (concise | detailed | bullet_points)

## RTA + Coherence Metadata
Includes full RTA discovery block and coherence emission hooks as defined in t401 MCP Bridge Templates.

## Usage
Can be called directly or via CoherenceMonitorBridge as a native tool.