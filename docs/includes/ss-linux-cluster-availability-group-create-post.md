---
ms.openlocfilehash: 0cdc343bf4ea6866d1a55672187451a3b6d95ec1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68215573"
---

## <a name="add-a-database-to-the-availability-group"></a>Hinzufügen einer Datenbank zu einer Verfügbarkeitsgruppe

Stellen Sie sicher, dass sich die Datenbank, die Sie der Verfügbarkeitsgruppe hinzufügen, im vollständigen Wiederherstellungsmodus befindet und eine gültige Protokollsicherung hat. Wenn es sich um eine Testdatenbank oder eine neu erstellte Datenbank handelt, nehmen Sie eine Datenbanksicherung vor. Führen Sie auf dem primären SQL Server das folgende Transact-SQL-Skript aus, um eine Datenbank mit dem Namen `db1` zu erstellen und zu sichern:

```sql
CREATE DATABASE [db1];
ALTER DATABASE [db1] SET RECOVERY FULL;
BACKUP DATABASE [db1] 
   TO DISK = N'/var/opt/mssql/data/db1.bak';
```

Führen Sie auf dem primären SQL Server-Replikat das folgende Transact-SQL-Skript aus, um einer Verfügbarkeitsgruppe mit dem Namen `ag1` eine Datenbank mit dem Namen `db1` hinzuzufügen:

```sql
ALTER AVAILABILITY GROUP [ag1] ADD DATABASE [db1];
```

### <a name="verify-that-the-database-is-created-on-the-secondary-servers"></a>Sicherstellen, dass die Datenbank auf den sekundären Servern erstellt wird

Führen Sie auf jedem sekundären SQL Server-Replikat die folgende Abfrage aus, um festzustellen, ob die `db1`-Datenbank erstellt und synchronisiert wurde:

```sql
SELECT * FROM sys.databases WHERE name = 'db1';
GO
SELECT DB_NAME(database_id) AS 'database', synchronization_state_desc FROM sys.dm_hadr_database_replica_states;
```
