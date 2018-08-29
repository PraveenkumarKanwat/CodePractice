# README
### Files given below are responsible to send you the rollup emails which you receive on a regular basis and their function are given below.
#### These scripts are present on the `rts-db001.sliad.dataxu.net` after that it is present in `sudo su - dataxu` and in `bin/`.

>**BUDGET_ROLLUP_TMP** : this is a file where budget rollup is stored temporarily 

>**send_rollup.py** : this file is responsible to send the emails to the recipients included in this file. It takes arguments such as `hostname`, `username`, `prefix` and `message` using these it forwards an email with attachment if available.

>**loaded-budget-report.sh** : runs before `loaded-budget-email.py` and collects detailed data by running a psql script

>**loaded-budget-email.py** : this file is responsible to extract the summary of the data by running a psql script and then triggers `send_rollup.py` with params. The mail which has a subject `RTS revenue rollups as of ...` is received because of this.

>**budget-report.sh** : runs before `budget-email.py` and collects detailed data by running a psql script

>**budget-email.py** : this file is responsible to collect the summary of the data by running a psql script and then triggers `send_rollup.py` with params. The mail which has a subject `RTS media spend rollups as of ...` is received because of this.

>**backup_rtsdb.sh** : hourly RTS DB backup job

>**s3copyhourly.sh** : hourly RTS DB local dump copied to s3

>**cleanBudgetLoaded.sh** : expire budget/loaded files

>**clean_budget_backups.sh** : hourly RTS DB local dump copied to s3

>**expire_rtsdb.sh** :  expire db dumps older than 3 days

>**crontab** : the currently used crontab in db001. This file may not be visible on the server but can be seen using `crontab -l` 

##### Other files include older version or not currently in used version or outdated version of the files.
