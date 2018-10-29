# batch5_phenix


## Loading data (under Ubuntu)

Install SQL Server Express Edition:

https://docs.microsoft.com/en-us/sql/linux/quickstart-install-connect-ubuntu?view=sql-server-2017

Restore the database backup:
```shell
sudo apt-get install p7zip-full
7z x PHX_D4G.7z 
sudo mv PHX_D4G.bak /var/opt/mssql/data/
sqlcmd -S localhost -U SA
```

```sql
use master
restore database PHX_D4G from disk='PHX_D4G.bak' 
with move 'PHX_D4G' to '/var/opt/mssql/data/PHX_D4G.mdf',
move 'PHX_D4G_log' to '/var/opt/mssql/data/PHX_D4G_log.ldf'
GO
```
