## Scheduling and Automation with Cron

You already know that scheduling and automation is one of the backbones of data engineering.

Manual execution doesn’t scale, automation ensures consistency, reliability, and timeliness. As an engineer, you should always be thinking in automation.

Once your Bash scripts are reliable, the next step is to run them automatically, at specific times, intervals, or based on events, without manual intervention.

Let's just look at some scenarios why scheduling is important in Data Engineering:

| Task                   | Frequency         | Example                        |
| ---------------------- | ----------------- | ------------------------------ |
| ETL pipeline execution | Daily at midnight | Load fresh data into warehouse |
| Log rotation           | Hourly            | Archive or compress logs       |
| Data sync with APIs    | Every 30 minutes  | Fetch new data from API        |
| Backups                | Weekly            | Save snapshots of databases    |

Performing these task manually is almost impossible.

### What is Cron?

- Cron is simply a time-based job scheduler in Unix/Linux systems.
- The cron daemon (crond) runs in the background and checks scheduled jobs.

Each cron job is defined in a **crontab file** (cron table) with this format:
```sql
* * * * * /path/to/command
| | | | |
| | | | └── Day of week (0–6, 0=Sunday)
| | | └──── Month (1–12)
| | └────── Day of month (1–31)
| └──────── Hour (0–23)
└────────── Minute (0–59)
```

For example:

| Schedule         | Description                                 |
| ---------------- | ------------------------------------------- |
| `0 0 * * *`      | Every day at midnight                       |
| `30 2 * * 1`     | Every Monday at 2:30 AM                     |
| `*/15 * * * *`   | Every 15 minutes                            |
| `0 */6 * * *`    | Every 6 hours                               |
| `0 9-17 * * 1-5` | Every hour between 9 AM–5 PM, Monday–Friday |

You don't need to memorize all this. There is a super useful website that helps us write cron expression interactively - https://crontab.guru/

### Commands to Mmange Cron Jobs

**View Your Crontab**
```bash
crontab -l
```

**Edit Your Crontab**
```bash
crontab -e
```
This opens your user’s crontab in the default text editor.

**Remove All Cron Jobs**
```bash
crontab -r
```
I don't need to tell you to becareful with this command.

Suppose you have a script `/home/najeeb/scripts/daily_etl.sh`, let's schedule it using `cron`:

**Make it executable** (Always remeber this):
```bash
chmod +x /home/najeeb/scripts/daily_etl.sh
```
**Schedule it**:
```bash
crontab -e
```
**Add**
```bash
0 2 * * * /home/najeeb/scripts/daily_etl.sh
```
This runs the ETL job daily at 2 AM.

