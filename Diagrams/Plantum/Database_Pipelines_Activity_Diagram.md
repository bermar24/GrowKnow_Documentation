@startuml
skinparam handwritten true
skinparam monochrome true
skinparam backgroundcolor white

title Activity Diagram: Manage Database & Pipelines

start

partition "Database Management" {
:Administrator applies schema migrations;
if (Migration successful?) then (Yes)
:Database schema is up to date;
else (No)
:System reports migration failure;
:Alert recorded for administrator review;
endif

:Administrator creates database backup;
if (Backup successful?) then (Yes)
:Backup file is stored;
else (No)
:System records backup failure;
:Backup scheduled for retry;
endif

:Administrator restores database from latest backup;
:Restore operation completes successfully;
}

partition "User Access Configuration" {
:Administrator grants user database-admin access;
:User has elevated database permissions;
}

partition "Pipeline Management" {
:Administrator starts data pipeline run "daily_ingest";
:Pipeline run completes with status "SUCCESS";
:Pipeline run logs contain "processed" and "completed";
}

end
@enduml