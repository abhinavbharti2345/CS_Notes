---
type: concept
topic: Programming Foundations
subtopic: Linux & Version Control
date: 2026-10-07
tags:
  - linux
  - git
  - devops
  - tools
---

# 🐧 Linux CLI & Git Version Control

> The essential operating environment and collaborative version-control foundation for software engineering and server management.

---

## 🎯 Why It Matters
- **Production Runs on Linux:** Almost 100% of cloud servers, Docker containers, and GPU clusters run Ubuntu/Debian/RHEL.
- **Git is the Source of Truth:** Essential for team collaboration, code reviews, automated CI/CD pipelines, and rollback mechanisms.
- **Diagnostic Power:** Command-line fluency allows you to triage live production bottlenecks (high CPU, memory leaks, disk fill-ups) in seconds.

---

## 🧠 Core Concepts

### 1. Essential Linux Utilities & Process Control
- **Navigation & Inspection:** `ls -la`, `cd`, `pwd`, `cat`, `less`, `find`, `grep -rn "pattern" .`
- **Process Management:** `ps aux`, `top`, `htop`, `kill -9 <PID>`, `pkill`, `systemctl status <service>`, `journalctl -u <service> -f`
- **Permissions & Ownership:** `chmod 755 script.sh`, `chown user:group file.txt`
- **Network Diagnostics:** `curl -iv https://api.com`, `netstat -tuln`, `ss -tulpn`, `ping`, `traceroute`, `ssh -i key.pem user@host`
- **Pipes & Streams:** `stdout (1)`, `stderr (2)`, `stdin (0)`, `cat log.txt | grep "ERROR" | awk '{print $4}' | sort | uniq -c`

### 2. Git Version Control Architecture
```text
Working Directory  ──(git add)──>  Staging Area  ──(git commit)──>  Local Repo  ──(git push)──>  Remote (GitHub)
```
- **Branching Strategies:** Feature branching, trunk-based development.
- **Rebase vs. Merge:**
  - `git merge`: Preserves complete commit history with a dedicated merge commit.
  - `git rebase`: Re-applies commits on top of another base tip, creating a linear history.
- **Resolving Conflicts:** Understanding conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`).

---

## 🗺️ Learning Order
1. Basic Linux navigation, file operations, and permissions (`chmod`, `chown`).
2. Text manipulation with `grep`, `sed`, `awk`, and pipe chaining.
3. Linux process lifecycle, signals (`SIGTERM`, `SIGKILL`), and systemd.
4. Git fundamentals: `init`, `clone`, `add`, `commit`, `status`, `diff`, `log`.
5. Git branching, merging, stash, cherry-pick, and rebase workflows.
6. SSH key creation, config management (`~/.ssh/config`), and remote server management.

---

## 🛠️ Practical Cheat Sheet

### Top Linux Diagnostic Commands
```bash
# Check memory and swap usage in human-readable format
free -h

# Check disk space usage
df -h

# Find open ports and listening processes
ss -tulpn

# Inspect live application logs in real-time
journalctl -u my-backend-service -f -n 100
```

### Git Interactive Rebase
```bash
# Clean up last 3 commits before submitting Pull Request
git rebase -i HEAD~3
```

---

## 🧪 Projects
- **Ubuntu Server Setup:** Configure an Ubuntu server with SSH keys, UFW firewall, Docker daemon, and automated systemd backup scripts.

---

## 🔗 Related Topics
- [[BrainOS/03 - Core CS/Operating Systems|Operating Systems Internals]]
- [[BrainOS/06 - Infrastructure/Docker & Kubernetes|Docker & Containerization]]
- [[BrainOS/04 - Software Engineering/Testing & CI-CD|CI/CD Pipelines]]
