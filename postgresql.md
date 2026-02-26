### Install

```bash
sudo apt install postgresql postgresql-contrib -y
sudo systemctl enable postgresql
sudo systemctl start postgresql
```

### Configure

```bash
# Switch to postgres user
sudo -u postgres psql

# Inside PostgreSQL shell:
CREATE USER myuser WITH PASSWORD 'your-strong-password-here';
CREATE DATABASE mydatabase OWNER myuser;
GRANT ALL PRIVILEGES ON DATABASE mydatabase TO myuser;

# Exit PostgreSQL
\q
```

Append to top of file `/etc/postgresql/16/main/pg_hba.conf`

```bash
local   mydatabase    myuser                     md5
```

Restart

```bash
sudo systemctl restart postgresql
```
