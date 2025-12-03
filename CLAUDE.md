# Claude Synology Manager

This repository is your workspace for managing a Synology NAS. It provides persistent context and memory for NAS administration tasks.

## Quick Reference

<!-- POPULATED BY FIRST-RUN INTAKE -->
| Field | Value |
|-------|-------|
| NAS IP (LAN) | _not configured_ |
| NAS IP (WAN) | _not configured_ |
| Model | _not configured_ |
| DSM Version | _not configured_ |
| Total Storage | _not configured_ |
| Available Storage | _not configured_ |
| SSH User | _not configured_ |

## First Run

If the Quick Reference above shows "_not configured_", run `/first-run` to populate NAS details via the intake agent.

## Your Capabilities

You can manage this NAS through:

1. **SSH** - Direct shell access for file operations, volume management, system commands
2. **MCP Tooling** - If a Synology MCP server is configured, use it for programmatic access

### Common Tasks

- **Shared Volumes**: List, create, modify, delete shared folders
- **Mounts**: Configure NFS and SAMBA mounts between this computer and the NAS
- **Storage**: Monitor disk usage, check RAID status, manage volumes
- **Backups**: Sync files, manage backup jobs
- **Permissions**: Set folder permissions and access controls

## Context Files

### Primary Context (Read on Every Session)

- `context/nas-profile.md` - Detailed NAS specifications and configuration

### Cached State (Update Periodically)

- `context/volumes/` - Snapshots of shared volume listings
- `context/mounts/` - Current mount configurations on this machine
- `context/storage-report.md` - Latest storage utilization report

### Update Context

When performing operations that change NAS state, update the relevant context files:

```bash
# After modifying shares, update volume snapshot
ssh <nas-user>@<nas-ip> "ls -la /volume1" > context/volumes/volume1.txt

# After changing mounts, capture current state
mount | grep <nas-ip> > context/mounts/current.txt
```

## Operational Guidelines

### Before Operations

1. Check `context/nas-profile.md` for connection details
2. Verify SSH connectivity: `ssh <user>@<nas-ip> "echo connected"`
3. Review relevant cached state in `context/`

### During Operations

1. Use SSH for direct file/system operations
2. Prefer non-destructive operations (list before delete, backup before modify)
3. Log significant changes for context updates

### After Operations

1. Update relevant context files with new state
2. If storage changed significantly, refresh `context/storage-report.md`
3. Commit context updates if substantive

## Scoped Operations

<!-- POPULATED BY FIRST-RUN INTAKE -->
The user has authorized the following operation categories:

- [ ] Volume management (create/delete shared folders)
- [ ] Mount configuration (NFS/SAMBA)
- [ ] File operations (copy, move, delete)
- [ ] Permission management
- [ ] System monitoring
- [ ] Backup operations

_Run `/first-run` to configure authorized operations._

## SSH Command Patterns

Common Synology SSH commands:

```bash
# List shared folders
ls /volume1/

# Check disk usage
df -h

# List running services
synoservice --list

# Check RAID status
cat /proc/mdstat

# View system info
cat /etc/synoinfo.conf
```

## Notes

_Space for session notes and observations:_

---
