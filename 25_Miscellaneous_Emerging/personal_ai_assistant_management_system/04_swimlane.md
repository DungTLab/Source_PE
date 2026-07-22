# Swimlane Diagram — Personal AI Assistant Management System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["End User"]
        U1["Submit Voice / Text Multimodal Prompt"]
        U2["Approve High-Risk Tool Action Prompt"]
        U3["Receive Streamed Response & Audio TTS"]
    end

    subgraph Lane2["System"]
        S1["Transcribe Voice STT & Scrub PII"]
        S2["Retrieve RAG Memory & Vector Docs"]
        S3{"Requires External Tool Call?"}
        S4["Format RAG Response & Synthesize TTS"]
        S5["Dispatch Execution Payload to Tool API"]
        S6["Format Tool Results into Final Response"]
    end

    subgraph Lane3["LLM Inference Engine"]
        L1["Process System Prompt & Context"]
        L2["Generate Reasoning & Tool Call JSON"]
        L3["Generate Final Answer Completion"]
    end

    subgraph Lane4["External Tool Execution Engine"]
        E1["Execute API Script (Calendar / Search)"]
        E2["Return Tool Execution Result Payload"]
    end

    Finish(["End"])

    Start --> U1 --> S1 --> S2 --> L1 --> L2 --> S3
    S3 -->|"No"| L3 --> S4 --> U3 --> Finish
    S3 -->|"Yes"| U2 --> S5 --> E1 --> E2 --> S6 --> L3
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | End User | Submits voice/text multimodal prompts (e.g. "Schedule team sync and check email"), approves high-risk tool execution prompts, and listens to synthesized TTS voice responses. |
| 2 | System | Transcribes speech to text, scrubs PII, retrieves RAG memory vectors, checks for tool calls, prompts user for confirmation, dispatches tool payloads, and synthesizes audio responses. |
| 3 | LLM Inference Engine | Ingests system prompt instructions + memory context, computes reasoning tokens, generates tool call JSON payloads, and produces final natural language completions. |
| 4 | External Tool Execution Engine | Receives authorized tool payloads, executes third-party API scripts (Google Calendar, Web Search, Home Assistant), and returns execution receipts. |
