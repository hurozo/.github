# Hurozo Agentic Platform Documentation

Welcome to Hurozo, an agentic platform that lets you visually build, share and run intelligent workflows. Build agents from reusable components, collaborate with others and expose your work through APIs.

### Environments
[![Development](https://img.shields.io/badge/Dev-staging.hurozo.com-informational)](https://staging.hurozo.com/)
[![Production](https://img.shields.io/badge/Prod-app.hurozo.com-success)](https://app.hurozo.com/)

## Getting Started

1. **Sign up** – Enter your email address on the sign‑in screen. You will receive a magic link; click it and you are in. No password or account creation is required.
2. **Create an agent** – A blank canvas appears when you start a new agent. Drag nodes from the 'components' menu and connect them to create your workflow.

## Capabilities

Hurozo provides a rich set of capabilities:

- Visual editor for constructing agents from modular nodes.
- Execution engine that runs your agent and streams results.
- Agent storage so you can save, version and reuse your work.
- Sharing and organization features for team collaboration.
- Export options for JSON definitions or ready‑to‑use HTTP APIs.
- Secret management for safely storing tokens and credentials.
- Remote nodes so you can extend the system with custom logic hosted elsewhere.

## Built‑in Nodes

Nodes are building blocks with typed inputs and outputs. Some commonly used categories include:

- **Basic & Arithmetic** – Add, subtract, multiply, divide and other fundamental operations.
- **Logic** – Conditional switches, equality checks and other flow‑control helpers.
- **Text & JSON** – Concatenate strings, split text, extract JSON fields and more.
- **HTTP & Web** – Make HTTP requests or work with webhooks.
- **Storage & Files** – Interact Dropbox, AWS S3 or Google Cloud Storage.
- **AI** – Call language models, sentiment analyses, image generators, and other AI tooling from various vendors
- **Widgets** – Build forms and UI elements for gathering user input.

Each node shows required and optional inputs. Connect compatible ports or enter default values in the properties panel.

## Building Agents from Components

1. Drag nodes from the component menu onto the canvas.
2. Connect outputs to inputs by dragging between their ports.
3. Right clicking a node allows you to define inputs and outputs. Configure node properties in the right‑hand panel. 
4. Press **Run** to execute the agent. The execution order follows the data flow.

### Defining Inputs

Add an **Input** node to expose fields that must be provided when the agent runs. Configure each field’s name, type and whether it is mandatory. At runtime these inputs appear in the input panel or API request body.

### Defining Outputs

Use the **Output** node to surface data produced by your workflow. Connect the final values to the Output node’s input ports. The values appear in the execution results.

## Exporting Agents

### Export as JSON

Choose **Export → JSON** to download a JSON file representing the agent. This includes all nodes, connections, inputs and outputs. You can import it later, store it for version control, or pass it around.

### Export as API

Select **Export → API** to generate Python code with your workflow embedded. Configure your API token and you'll be on your way.

#### Calling the Agent API

Send a POST request to the provided URL. The request body only needs the input values defined by your Input node; do **not** include the entire workflow definition. Example:

```bash
curl -X POST https://api.hurozo.com/execute/<agent-id> \
  -H "Authorization: Bearer <token>" \
  -H "Content-Type: application/json" \
  -d '{"user_text": "Hello"}'
```

The response contains the outputs defined in your Output node.

## Sharing and Collaboration

### Share Agents

Open the **Share** dialog on a saved agent and enter another user’s email address. Recipients can load and run the shared agent.

### Organisations

Create an organisation from your profile menu. Organisations provide a shared workspace with its own list of agents and secrets.

#### Invite Members

Within an organisation, open the **Members** panel and invite members by email. They need to have at least signed in once to be able to invite them. Organisation agents become visible to all members.

## Secrets Management

Use the **Secrets** panel to securely store API keys and other credentials. Define a key name and paste the value; examples:

- `OPENAI_API_KEY` – token for OpenAI services.
- `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` – AWS tokens.
- `DROPBOX_TOKEN` for Dropbox interaction
- `NOTION_TOKEN` to access the Notion API
- `VERTEXAI_API_KEY` to interact with GCP VertexAI Tooling

## Remote Nodes

Remote nodes let you extend Hurozo with custom logic hosted outside the platform.
You'll find an example remote node in the 'nodes' repository.
After registration, the node becomes available in the component menu. Drag it into workflows and provide the necessary inputs.
When executed, Hurozo sends the input payload to your service, waits for the response and passes the results downstream.

## Reusing Saved Agents as Nodes

Saved agents can act as standalone nodes:

1. Save an agent after defining its Input and Output nodes.
2. In a new workflow, find the saved agent under the **Agents** section of the components menu.
3. Drag it onto the canvas. The agent appears as a node with the inputs and outputs you defined.
4. Connect it like any other node to reuse complex functionality.

## Final note
Hurozo empowers you to craft intelligent agents, share them with collaborators and expose them as APIs. Use built‑in nodes, remote extensions and secrets to assemble powerful workflows without writing code.

Happy building!
