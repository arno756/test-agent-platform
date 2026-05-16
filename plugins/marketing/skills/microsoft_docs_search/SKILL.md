---
name: microsoft_docs_search
description: Use this skill when the user asks technical questions about Microsoft products, frameworks, or cloud services, or needs official documentation, best practices, or reference material.
---

# Skill: Microsoft Learn Documentation Search

## Tool Integration
**Tool Name:** `microsoft_docs_search`
**Endpoint (if required by host):** `https://learn.microsoft.com/api/mcp`

## Instructions for the Agent
1. **Analyze:** Identify the core technology and concept the user is asking about (e.g., "Azure Cosmos DB vector search").
2. **Search:** Invoke the `microsoft_docs_search` tool with a concise, targeted search query. Avoid overly long sentences; use keyword-rich phrases.
3. **Review & Fetch:** Review the returned search results. If a specific page appears highly relevant but more detail is needed, use `microsoft_docs_fetch` (if available) to read the full page content.
4. **Synthesize:** Construct your response using the retrieved information. Ground your technical guidance in the facts provided by the MCP server.
5. **Cite:** **Always** include a markdown link back to the official Microsoft Learn URL provided in the search results so the user can verify the information.

## Execution Examples

### Example 1: Concept Lookup
**User Prompt:** "What are the consistency levels available in Azure Cosmos DB?"
**Agent Action:** Invoke `microsoft_docs_search` with the query `"Azure Cosmos DB consistency levels"`.

### Example 2: API Reference
**User Prompt:** "How do I configure a minimal API in ASP.NET Core?"
**Agent Action:** Invoke `microsoft_docs_search` with the query `"ASP.NET Core minimal API configuration tutorial"`.

### Example 3: CLI Troubleshooting
**User Prompt:** "What is the az cli command to restart a web app?"
**Agent Action:** Invoke `microsoft_docs_search` with the query `"az webapp restart command reference"`.

## Constraints & Guardrails
- **No Hallucinations:** Do not rely solely on internal training data for specific parameter names, API versions, or pricing. Always attempt to ground the response using the `microsoft_docs_search` tool first.
- **Fallback:** If the search returns no results, automatically try broadening the search term (e.g., remove version numbers) before informing the user that the documentation could not be found.