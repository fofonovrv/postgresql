# Шаблон для развертвания обзазов postgre + pgadmin

### После развернтывания контейнеров необходимо поправить права:
```
# в папке с docker-compose.yml
sudo chown -R 5050:5050 $pgadmin
```

### Postgesql DB 13.3
Параметры:
```
      - "max_connections=50"
      - "shared_buffers=1GB"
      - "effective_cache_size=4GB"
      - "work_mem=16MB"
      - "maintenance_work_mem=512MB"
      - "random_page_cost=1.1"
      - "temp_file_limit=10GB"
      - "log_min_duration_statement=200ms"
      - "idle_in_transaction_session_timeout=10s"
      - "lock_timeout=1s"
      - "statement_timeout=60s"
      - "shared_preload_libraries=pg_stat_statements"
      - "pg_stat_statements.max=10000"
      - "pg_stat_statements.track=all"
```
```
      POSTGRES_DB: "testdb"
      POSTGRES_USER: "testdb"
      POSTGRES_PASSWORD: "testdb"
      PGDATA: "/var/lib/postgresql/data/pgdata"
      
      port 5432
```
Не забудьте ввести учетные данные от БД для healthcheck
``` test: ["CMD-SHELL", "pg_isready -U testdb -d testdb"] ```

### PGAdmin4 5.7 - графический веб интерфес для управления postresql
Переменные:
```
      PGADMIN_DEFAULT_EMAIL: "fofonovrv@gmail.com"
      PGADMIN_DEFAULT_PASSWORD: "testdb"
      PGADMIN_CONFIG_SERVER_MODE: "False"
      
      port 5050
```
