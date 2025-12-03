# Claude Synology Manager

[![Built with Claude Code](https://img.shields.io/badge/Built%20with-Claude%20Code-blue?logo=anthropic)](https://claude.ai/code)
[![Claude Code Projects](https://img.shields.io/badge/Claude%20Code-Projects%20Index-orange)](https://github.com/danielrosehill/Claude-Code-Repos-Index)
[![GitHub Master Index](https://img.shields.io/badge/GitHub-Master%20Index-green)](https://github.com/danielrosehill/Github-Master-Index)

A workspace repository for Claude Code to manage a Synology NAS. This repo serves as persistent memory and operational context for NAS administration tasks.

## Purpose

This repository provides Claude with:

- **Persistent context** about your NAS configuration (model, storage layout, shared volumes)
- **Operational workspace** for managing mounts, shares, and file operations
- **Memory storage** for NAS-specific details that persist between sessions

## How It Works

When you open this repository with Claude Code, Claude has immediate access to:

1. **NAS profile** (`context/nas-profile.md`) - Hardware specs, IP addresses, storage configuration
2. **Volume snapshots** (`context/volumes/`) - Periodic captures of shared volume states
3. **Mount configurations** (`context/mounts/`) - Current NFS/SAMBA mount definitions

Claude uses SSH or MCP tooling to interact with the NAS and keeps this context updated.

## First Run

On first use, run the intake command to populate your NAS details:

```
/first-run
```

This will prompt you for:
- NAS IP address (LAN and/or WAN)
- SSH credentials or MCP configuration
- Scope of operations you want Claude to perform

## Directory Structure

```
.
├── CLAUDE.md              # Instructions for Claude
├── README.md              # This file
├── context/
│   ├── nas-profile.md     # NAS hardware and network details
│   ├── volumes/           # Shared volume snapshots
│   └── mounts/            # Mount configuration records
└── .claude/
    ├── commands/          # Slash commands
    └── agents/            # Subagents for specialized tasks
```

## Common Operations

Once configured, you can ask Claude to:

- **List shared volumes**: "Show me all shared folders on the NAS"
- **Check disk usage**: "How much space is left on the NAS?"
- **Manage mounts**: "Mount the media share to ~/media"
- **Configure shares**: "Create a new shared folder called backups"
- **Backup operations**: "Sync my documents folder to the NAS"

## Requirements

- SSH access to your Synology NAS, OR
- Synology MCP server configured in Claude Code

## Template Usage

This repository is designed as a GitHub template. Fork or use as template to create your own NAS management workspace.

## License

MIT

---

*To view an index of my Claude Code related projects, [click here](https://github.com/danielrosehill/Claude-Code-Repos-Index).*
