# Working with Claude Code Agent

## Get started
- Take the server snapshot
- SSH to the server
- Make sure you are logged in as Agent/user dedicated account
- create a new project/folder
- type claude


## Understand the agent environment
In the Claude working directory(the project/folder) there are 
#### 1. Default behavior 
- By default Claude can read and write files within your current directories and its subdirectories

#### 2. The file .claudeignore in the root directory
- It respect the file `.claudeignore` (with the similar syntax as `.gitignore`) where you specify the files you don want it to touch.

#### 3. The file CLAUDE.md in the root directory
This is the onboarding documentation written for Claude.
With this file you give claude persistent instructions about your project:
- Test tech you are using
- Naming conventions for your team follows
- which script to run before deploying
- Command it should never run, etc...

You write it once and every session claude read it automatically.

A common approch is to let claude generate its own CLAUDE.md

*Example1*:\
Explore this repo and generate a CLAUDE.md file for it.

*Example1*:\
Create a CLAUDE.md based on our project structure and conventions.

You can add any precision

#### 4. Manually run a shell command inside claude
You just need to add `!`before the command

```bash
! pwd                                                                                                                                   
  ⎿  /home/claude-agent
```

## Agent skills
Find Documentation [here](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview)

#### 1. Definition
Agent Skills are modular capabilities that extend Claude's functionality. Each Skill packages instructions, metadata, and optional resources (scripts, templates) that Claude uses automatically when relevant.

#### 2. Why use Skills ?
Skills are reusable, filesystem-based resources that provide Claude with domain-specific expertise: workflows, context, and best practices that transform general-purpose agents into specialists.

#### 3. Using Skills
Anthropic provides pre-built Agent Skills for common document tasks (PowerPoint, Excel, Word, PDF), and you can create your own custom Skills. Both work the same way. Claude automatically uses them when relevant to your request.

Pre-built Agent Skills are available on claude.ai, the Claude API, Claude Platform on AWS, and Microsoft Foundry.