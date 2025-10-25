## Sorting, Counting, and Filtering Data

Important Linux commands for data processing.

| Command | Description                    | Example                               |
| ------- | ------------------------------ | ------------------------------------- |
| `sort`  | Sort lines alphabetically      | `sort names.txt`                      |
| `uniq`  | Remove duplicates              | `uniq names.txt`                 |
| `wc`    | Count lines/words/chars        | `wc -l file.txt`                      |
| `cut`   | Extract columns by delimiter   | `cut -d',' -f2 data.csv`              |
| `awk`   | Pattern scanning and reporting | `awk -F',' '{print $1, $3}' data.csv` |
| `sed`   | Stream editor (search/replace) | `sed 's/old/new/g' file.txt`          |


**Example**: Count number of failed jobs in a log file
```bash
grep "FAILED" job_logs.txt | wc -l
```
