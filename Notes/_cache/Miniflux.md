## On Ubuntu 22 ARM[^4][^5][^6][^7]

```sh
cd /etc/apt/sources.list.d
sudo touch miniflux.list
echo "deb [trusted=yes] https://repo.miniflux.app/apt/ * *" | sudo tee /etc/apt/sources.list.d/miniflux.list > /dev/null
sudo apt update
sudo apt install miniflux
sudo apt install postgresql-common
sudo /usr/share/postgresql-common/pgdg/apt.postgresql.org.sh
sudo apt install postgresql-16
sudo -u postgres psql
```

```sh
CREATE USER miniflux WITH ENCRYPTED PASSWORD 'miniflux';
CREATE DATABASE miniflux;
GRANT ALL PRIVILEGES ON DATABASE miniflux TO miniflux;
ALTER USER miniflux WITH SUPERUSER;
\q
```

```sh
sudo vim /etc/miniflux.conf
```

```
RUN_MIGRATIONS=1
DATABASE_URL=user=miniflux password=miniflux dbname=miniflux sslmode=disable
LISTEN_ADDR=/run/miniflux/miniflux.sock
PORT=8070
```

```sh
miniflux -c /etc/miniflux.conf -migrate
miniflux -c /etc/miniflux.conf -create-admin
# sudo systemctl start postgresql
miniflux -c /etc/miniflux.conf
```

```sh
sudo systemctl enable --now miniflux
sudo systemctl enable --now postgresql
```

## On Windows 10

1. Get `miniflux-windows-amd64` from [releases](https://github.com/miniflux/v2/releases), rename it to `miniflux.exe`.
2. [PostgreSQL](https://www.postgresql.org/) (test on v14).

Create database[^1]:

```sh
initdb --locale=C --username=miniflux --pgdata=miniflux
postgres -D miniflux
# Keep this terminial window
```

Configrate database[^2]:

1. Find and run `pgAdmin4.exe`.
2. Servers → Context-menu → Register → Server → Tab `General`:
   ```
   Name: miniflux_server
   ```
3. Tab `Connection`:
   ```
   host name: localhost
   Maintenance database: miniflux
   Username: miniflux
   ```
4. Servers → miniflux_server → Context-menu of `Databases` → Create → Database → Tab `General`:
   ```
   Database: miniflux
   ```
5. Tab `Definition`:
   ```
   Encoding: None
   ```

Create `miniflux.conf`[^3]:

```
DATABASE_URL=user=miniflux password=secret dbname=miniflux sslmode=disable
RUN_MIGRATIONS=1
POLLING_FREQUENCY=60
CREATE_ADMIN=1
ADMIN_USERNAME=<admin_username>
ADMIN_PASSWORD=<admin_password>
DEBUG=on
WORKER_POOL_SIZE=10
PORT=8070
```

```sh
# In a new terminal session
miniflux -config-file miniflux.conf
```

## Usage

```sh
# Backup data
pg_dump -U miniflux -h 127.0.0.1 -p 5432 -F t miniflux > miniflux.tar
```

```sh
# Clear postgresql
sudo systemctl stop postgresql
sudo systemctl disable postgresql
pg_lsclusters
sudo systemctl stop postgresql@16-main
sudo pg_dropcluster 16 main --stop
sudo apt-get remove --purge postgresql-16
```

## Autorun at startup on Windows 10

1. Create `start_miniflux.bat`.
   ```batch
   rem Maybe need administrator permissions. I forgot.
   @echo off
 
   start postgres.exe -D miniflux_db
   timeout 5
   start miniflux.exe -config-file miniflux.conf
 
   pause
   ```
2. I don't want to use `Windows Task Scheduler`. I don't try [NSSM](https://nssm.cc/). So create `start_miniflux.vbs`:
   ```vbs
   Set WshShell = CreateObject("WScript.Shell")
     WshShell.Run chr(34) & "<path_to>\start_service.bat" & Chr(34), 0
   Set WshShell = Nothing
   ```
3. Create shortcut of `start_miniflux.vbs`.
4. Put the shortcut into `C:\Users\User\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup\`.

[^1]: [initdb](https://www.postgresql.org/docs/current/app-initdb.html)
[^2]: [Server Dialog](https://www.pgadmin.org/docs/pgadmin4/development/server_dialog.html)
[^3]: [Configuration Parameters](https://miniflux.app/docs/configuration.html)
[^4]: [Debian Installation](https://miniflux.app/docs/debian.html)
[^5]: [How do I solve this problem to use psql? | psql: error: FATAL: role "postgres" does not exist](https://stackoverflow.com/questions/65222869/how-do-i-solve-this-problem-to-use-psql-psql-error-fatal-role-postgres-d)
[^6]: [How To Completely Uninstall PostgreSQL](https://kb.objectrocket.com/postgresql/how-to-completely-uninstall-postgresql-757)
[^7]: [Linux downloads (Ubuntu)](https://www.postgresql.org/download/linux/ubuntu/)