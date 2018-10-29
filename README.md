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

Driver pour se connecter depuis python :

https://docs.microsoft.com/en-us/sql/connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server?view=sql-server-2017

(Le nom du driver installé se trouve dans dans `/etc/odbcinst.ini`.)

```python
import pyodbc
con = pyodbc.connect('DRIVER={ODBC Driver 17 for SQL Server};SERVER='+server+';DATABASE='+database+';UID='+username+';PWD='+ password)
```
