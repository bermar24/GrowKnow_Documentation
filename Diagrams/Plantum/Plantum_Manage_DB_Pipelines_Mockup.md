@startsalt
{+
{* File | Edit | Help }
{/ <b>Pipelines</b> | Database | Backups | Logs }
{
.
Main Panel: Database & Pipelines Management
.
{#
<b>Pipeline Name</b> | <b>Status</b> | <b>Last Run</b> | <b>Actions</b>
Daily Ingest | [green check] Success | 2023-10-27 08:00 | [Run Now] [Edit] [Log]
User Sync | [blue spin] Running | 2023-10-27 10:15 | [Stop] [Edit] [Log]
Model Training | [red X] Failed | 2023-10-26 12:00 | [Run Now] [Edit] [Log]
}
---
<b>Database Health:</b> [Healthy (Green)] | <b>Storage:</b> 1.2GB / 5GB
[Apply Migrations] | [Create Backup] | [Manage Access]
}
{
<b>Recent Logs</b>
{
[2023-10-27 10:16] INFO: Starting user sync...
[2023-10-27 10:17] WARN: Connection latency high.
[2023-10-27 10:18] INFO: Processed 450 records.
}
[Download Logs] | [Clear View]
}
}
@endsalt