## File Content Search and Text Processing

Linux provides commands for searching and filtering text, which are essential for handling logs and datasets.

| Command   | Description                  | Example                           |
| --------- | ---------------------------- | --------------------------------- |
| `grep`    | Search for text              | `grep "error" app.log`            |
| `grep -i` | Case-insensitive search      | `grep -i "data" report.txt`       |
| `grep -r` | Recursive search             | `grep -r "pipeline" /opt/airflow` |
| `find`    | Locate files by name or type | `find /var -name "*.log"`         |

