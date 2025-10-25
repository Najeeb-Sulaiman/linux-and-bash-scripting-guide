## Environment Variables

Environment variables are used to store system or user-specific settings.

| Command            | Description                    | Example                 |
| ------------------ | ------------------------------ | ----------------------- |
| `echo $PATH`       | Show executable search path    |                         |
| `export VAR=value` | Set a variable                 | `export DATA_DIR=/data` |
| `env`              | List all environment variables |                         |

**For example:**
```bash
export AIRFLOW_HOME=/opt/airflow
export SPARK_HOME=/usr/local/spark
```

