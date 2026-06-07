# Using Claude in automation

## Use case 1 : Use a Pipe to run command

```bash
$ claude --help

...
  -p, --print                           Print response and exit (useful for
                                        pipes). Note: The workspace trust dialog
                                        is skipped when Claude is run in
                                        non-interactive mode (via -p, or when
                                        stdout is not a TTY, e.g. piped or
                                        redirected output).
...
```

Exemple:

```bash
$ claude -p "Give me a single bash command to fully update this Ubuntu system and install vim, neovim and unzip using DEBIAN_FRONTEND=noninteractive. Output only the command, no explanation, no markdown, only the command" | sudo bash
``` 

## Use case 2 : Use a Pipe to analyse a config file

```bash
$ cat nginx.conf | claude -p "Review this nginix config for security issues ans misconfigurations"
```

- The result comes back to the terminal in plain text.

```bash
$ claude -p "Review this nginix config for security issues ans misconfigurations" < nginx.conf
```
- This will provide same result


## Use case 3: Use Claude in a pipeline

Let's say you have a pipeline that generates logs and stores it in deploy.log.

- You can add a step with the following instruction:

```bash
$ tail -n 100 deploy.log | claude -p "Summirize any errors or warnings from this deployment log in plain english"
```

You can post the summary in log file, Slack channel or in a opened ticket.

- You can get the out in json format instead of default plain text

```bash
$ cat server_report.json | claude -p "List any critical issues found" --output-format json
```

## User case 4: Compare files with claude

```bash
$ claude -p "compare these two configs and explain the difference - first is prod, second is staging:
$(cat prod.yaml)
---
$(cat staging.yaml)"
```

Or

```bash
$ diff prod.yaml staging.yaml | claude -p "Explain these config differences in plain English and flag anything that looks like drift or misconfigured"
```

## Use case 5: Whitelist allowed tools to use by claude (Permissions)

- Reads and Greps are allowed
```bash
$ cat app.py | claude -p "Review for security issues" --allowedTools "Read,Grep"
```

- Bash is not allowed. So Claude cannot run commands
```bash
$ cat deploy.sh | claude -p "Analyze this script" --disallowedTools "Bash"
```

## Use case 6: Claude exit code
Claude returns non-zero code on failure

In pipelines, take in account that claude can fail.

```bash
$ cat config.yaml | claude -p "validate this config" --output-format json && echo "Analysis complete" || echo "Claude code failed"
```

# Using Claude as Non interactive agent: --dangerously-skip-permissions
- `claude -p` does not run any command on the system. you use pipes, commands or redirections to use its outputs.
- In the case of `claude --dangerously-skip-permissions`, Claude has all permissions "Bash", "Read", etc
- It actually runs commands on your system in a non interactive mode
- that is why its environment must correctly set up to be under control.

```bash
$ claude --dangerously-skip-permissions "Check disk usage on all mount points anf generate a report file in the current directory."
```

- This will actually run and create a file on the system without any confirmation from the user






