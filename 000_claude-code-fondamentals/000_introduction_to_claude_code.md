# Introduction to claude code

## What is claude code ?

#### Key idea
Claude code participates in the development workflow, `Not just generates code`

#### 1. Agentic Tool
It understand your entire projects, midifies files, runs commands end to end.

#### 2. Git integration
I can stage changes, write commit messages, create branches, opens pull requests

#### 3. CI / Automation
In automation senarios, it can plugs into pipelines to review code, triage issues, genarate fixes.

#### 4. And more advanced workflows
It can:

- Run tasks in isolation
- Execute multiple steps in sequence
- Opererate in non interactive mode

In more advanced setup, you can define specialized agents for different responsabilities such as `testing`, `security` or `architecture review`


## How Claude code works ?
#### a. Agent is local
Claude code agent runs in your terminal or IDE, reads files, executes commands on your system.

#### b. Intelligence is on the cloud
When claude code needs reasonning, it sends context to the Claude API; The model processes the request, reasons and returns instructions. Those instructions are executed locally.

#### c. Hybrid architecture
Claude code is a hybrid architecture, NOT just a fully self-hosted system: **Local execution + Cloud reasoning**


## Where can we run Claude code ?
It can run in multiple environments:

#### 1. CLI
This is the most important for serious work (DevOps, Automation and Agents)
- It runs in your terminal.
- This is the must powerful mode because it allows agent to interact directly with your filesystems and executes commands

#### 2. IDEs
- We cans also use it in the IDEs like `Cursor`, `WinSurf` or `VS Code`
- With these environments, you get features like: **Inline diffs**, **Conversation history** and **easier code review**

#### 3. Browser
In the browser based version, we can work with repositories without setting up a loacal environment

#### 4. NOTE
Claude code can be installed on any machine where you do development.
- On your Laptop
- On a remote server such as a Linux VPS (VERY COMMON if you want to work on productions systems, automate infrastructures or keep your environment always running)
- Inside containers for isolation
- Integrated into CI/CD pipelines for automation


