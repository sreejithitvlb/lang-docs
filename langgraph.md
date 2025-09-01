# Langgraph

Develop, deploy, scale, and manage agents

## Agent Definition

We have to define the Agent, which has many tools/nodes created by us.

## Components of Langgraph

- **Server**: Execution environment for agentic workflows | running the workflows
- **CLI**: Command-line interface to interact with the server (optional) | deploying the workflows
- **Studio**: Visualizing the agentic workflows | visualizing the workflows
- **SDK**: Building the agentic workflows
- **Remote Graph**: Agent in server | automates agentic communication
	- How does it work locally vs. in the server?
	- The code structure is the same, but deployment is different. Locally, you can make `agent.invoke` a tool to test.
- **Control Plane**: CNS of the langgraph server | orchestrator | hidden for the developer | manager uses data plane
- **Data Plane**: Data supporter of control plane | workforce used by control plane


## Terminology

| Term / Symbol                  | Description                                                                                              |
|--------------------------------|----------------------------------------------------------------------------------------------------------|
| App                            | One agent, one workflow, many tools                                                                      |
| Server                         | Hosts many apps                                                                                          |
| Agent                          | Component in an App (one per App)                                                                        |
| Graph                          | Workflow representation of the server (one graph ↔ one agent)                                           |
| Remote Agent                   | Remote agent running in the server                                                                       |
| Routing Decision               | Logic that selects the next node (edge)                                                                  |
| State                          | Data/outcome produced by node execution; drives routing decisions                                        |
| Checkpoints                    | Saved snapshots of graph state for rollback or review                                                    |
| Human-in-Loop                  | Points where human intervention is required (often tied to checkpoints)                                   |
| Node                           | A computation unit inside the graph                                                                      |
| Tools                          | Deterministic functional nodes that wrap external APIs or logic                                          |
| LLMNode                        | Node implemented by an LLM (non-deterministic / generative)                                              |
| ConditionalNode                | Node that inspects state and chooses which branch to take                                                |
| Custom Function Node           | User-defined code-first node (similar to Tools)                                                          |
| Interruptions                  | Special edges that pause execution and require human-in-loop                                             |
| Streaming                      | Long-running nodes that emit realtime updates (callbacks / streams)                                      |
| TavilySearchResults            | External search/retrieval component (do not rely solely on pre-trained models)                           |
| `langchain/core/tools`         | Location to define and register custom tools                                                              |
| `langchain/langgraph/prebuilt` | Prebuilt ToolNode implementations (tool-backed nodes without embedded LLMs)                              |
| `MemorySaver`                  | Utility for persisting checkpoints and graph state                                                       |
| `HumanMessage`                 | Wrapper for passing human-provided messages into LLMs                                                    |
| `CreateReactAgent`             | Factory that composes tools and an LLM into a runnable agent                                             |
| `StateGraph`                   | API for constructing and managing graphs and state transitions                                            |
| `Reflection`                   | Helper for post-processing or inspecting execution results                                                |
| `ToolCalling`                  | Pattern and utilities for LLM → tool invocation and result handling                                      |


