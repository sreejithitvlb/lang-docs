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

| Term                  | Description                                                      |
|-----------------------|------------------------------------------------------------------|
| App                   | One agent, one workflow, many tools                              |
| Server                | Hosts many apps                                                  |
| Agent                 | Component in App, one per App                                    |
| Graph                 | Workflow representation of server, one graph-one agent           |
| Remote Agent          | Remote agent in the server, enables agentic communication        |
| Routing Decision      | Logic to pick next node (edge)                                   |
| State                 | Outcome/data; node execution → state change → routing decision   |
| Checkpoints           | Saved version of a graph state                                   |
| Human-in-Loop         | Human intervention after checkpoints                             |
| Node                  | Graph entity                                                     |
| Tools                 | Type of node, deterministic outcome                             |
| LLMNode               | Type of node, LLM outcome                                        |
| ConditionalNode       | State inspection, decides which node to call next                |
| Custom Function Node  | Similar to Tools, without tool function wrapper (you vs LLM)     |
| Interruptions         | Special type edge, requires human-in-loop, saved as checkpoint   |
| Streaming             | Realtime updates, long running processes, like callback          |
