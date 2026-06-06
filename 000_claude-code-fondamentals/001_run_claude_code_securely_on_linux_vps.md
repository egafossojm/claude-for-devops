# Run Claude code securely on a Linux VPS
We are using a Ubuntu VPS in this case

### 1. Create a dedicated user/agent and with sudo access
- Never run claude code as root

```bash
useradd -m -shell /bin/bash -c 'Claude Code User' claude-agent
usermod -aG sudo claude-agent
```

#### 2. Use No Password for the agent
- So claude can run privileged commands too.
- Claude code cannot type a password interactively
- If a sudo command requires a password, it will fail.
- Every sudo call gets logged in var.log, auth.log

```bash
echo "claude-agent ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/claude-agent
```

#### 3. Take a snapshot of the vps before any cloud code session on real server
- Always snapshot before a session
- Take this as your UNDO button

#### 3. Run cloud code inside TMAX or SCREEN to keep sessions alive when you disconnect
This allows claude to keep running even your SSH session gets interrupt
- Connect to the server via ssh
- start a new screen session
```bash
screen

# or 

screen -S session_name
```
- To detach from a session: `Press Ctrl+a then d`.
- To view active screens
```bash
screen -ls
```
- To reattach to a session
```bash
 screen -r session_name 

 # or if it's the only one active).

 screen -r
 ```




