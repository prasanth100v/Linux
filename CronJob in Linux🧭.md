### ✅ What is a Cron Job?

A cron job is a scheduled task that runs automatically at a fixed time or interval (minutes, hours, days, etc.).

Examples:

Run a backup every night

Clean logs every week

Restart a service daily


###  Cron job syntax (very important)
```
* * * * * command_to_run
│ │ │ │ │
│ │ │ │ └── Day of week (0–7) (Sun=0 or 7)
│ │ │ └──── Month (1–12)
│ │ └────── Day of month (1–31)
│ └──────── Hour (0–23)
└────────── Minute (0–59)
```
