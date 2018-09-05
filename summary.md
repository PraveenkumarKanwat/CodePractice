# Overview
Files given below are responsible for sending the rollup emails which will be received on a regular basis.
These scripts are located on `rts-db001.sliad.dataxu.net` under `/opt/dataxu/dxuser/bin/` for the `dataxu` user.

These scripts are not the part of `/opt/dxrts/bin/database/` folder but are located under `/opt/dataxu/dxuser/bin/`.

- **BUDGET_ROLLUP_TMP** : this is a file where budget rollup is stored temporarily and it is present only on the server.

- **[send_rollup.py](send_rollup.py)** : this file is responsible for sending the emails to the recipients mentioned in this file. It takes arguments such as `hostname`, `username`, `prefix` and `message` using these it forwards an email with attachment if available.

- **[loaded-budget-report.sh](loaded-budget-report.sh)** : runs before `loaded-budget-email.py` and collects detailed data by running a psql script.

- **[loaded-budget-email.py](loaded-budget-email.py)** : this file is responsible to extract the summary of the data by running a psql script and then triggers `send_rollup.py` with params. This script produces the email with `RTS revenue rollups as of ...` subject.

- **[budget-report.sh](budget-report.sh)** : runs before `budget-email.py` and collects detailed data by running a psql script

- **[budget-email.py](budget-email.py)** : this file is responsible for collecting the summary of the data by running a psql script and then triggers `send_rollup.py` with params. This script produces the email with `RTS media spend rollups as of ...` subject.

- **[backup_rtsdb.sh](backup_rtsdb.sh)** : hourly RTS DB backup job.

- **[s3copyhourly.sh](s3copyhourly.sh)** : hourly copies RTS DB local dump to S3.

- **[cleanBudgetLoaded.sh](cleanBudgetLoaded.sh)** : expire budget/loaded files.

- **[clean_budget_backups.sh](clean_budget_backups.sh)** : clean up RTS DB local dump older than 7 days.

- **[expire_rtsdb.sh](expire_rtsdb.sh)** :  removes db dumbs older than 3 days.

- **[crontab](/rts-dist/src/main/dxad_home/cron/masterDatabaseCrons)** : the currently used master database crontab in rts-db001. Currently crons are configured via crontab, so this file is not present on the host directly. 

Other files include older version or not currently in used version or outdated version of the files.

**Note:** If the files location are changed to `/opt/dxrts/bin/database/email-rollups/` from this `/opt/dataxu/dxuser/bin/` futher changes needed to be made like changing the dependency location of `send_rollup.py` in files `budget-email.sh` and `loaded-email-budget.sh` from `/opt/dataxu/dxuser/bin/send_rollup.py` to `/opt/dxrts/bin/database/email-rollups/send_rollup.py`.
