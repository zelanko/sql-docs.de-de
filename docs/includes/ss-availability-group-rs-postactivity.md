
## <a name="add-a-database-to-the-availability-group"></a>Hinzufügen einer Datenbank zu einer Verfügbarkeitsgruppe

Stellen Sie sicher, dass sich die Datenbank, die Sie der Verfügbarkeitsgruppe hinzufügen, im vollständigen Wiederherstellungsmodus befindet und eine gültige Protokollsicherung hat. Wenn die Datenbank eine Testdatenbank oder eine neu erstellte Datenbank handelt, nehmen Sie eine Datenbanksicherung vor. Führen Sie zum Erstellen und Sichern einer Datenbank namens `db1` das folgende Transact-SQL-Skript auf der primären SQL Server-Instanz aus:

```sql
CREATE DATABASE [db1];
ALTER DATABASE [db1] SET RECOVERY FULL;
BACKUP DATABASE [db1]
   TO DISK = N'/var/opt/mssql/data/db1.bak';
```

Führen Sie zum Hinzufügen einer Datenbank namens `db1` für eine Verfügbarkeitsgruppe namens `ag1` das folgende Transact-SQL-Skript auf dem primären SQL Server-Replikat aus:

```sql
ALTER AVAILABILITY GROUP [ag1] ADD DATABASE [db1];
```

### <a name="verify-that-the-database-is-created-on-the-secondary-servers"></a>Sicherstellen, dass die Datenbank auf den sekundären Servern erstellt wird

Führen Sie zum Anzeigen, ob die Datenbank `db1` erstellt und synchronisiert wurde, die folgende Abfrage auf allen sekundären SQL Server-Replikaten aus:

```sql
SELECT * FROM sys.databases WHERE name = 'db1';
GO
SELECT DB_NAME(database_id) AS 'database', synchronization_state_desc FROM sys.dm_hadr_database_replica_states;
```
