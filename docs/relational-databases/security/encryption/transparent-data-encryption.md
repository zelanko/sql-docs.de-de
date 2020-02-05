---
title: Transparente Datenverschlüsselung (TDE) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/09/2019
ms.prod: sql
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Transparent Data Encryption
- database encryption key, about
- TDE
- database encryption key
- TDE, about
- Transparent Data Encryption, about
- encryption [SQL Server], transparent data encryption
ms.assetid: c75d0d4b-4008-4e71-9a9d-cee2a566bd3b
author: jaszymas
ms.author: jaszymas
ms.reviewer: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 498fe2391cd3e8109aed3f6e1e02436234ffe6f7
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "74957324"
---
# <a name="transparent-data-encryption-tde"></a>TDE (Transparent Data Encryption)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  *Transparente Datenverschlüsselung* (Transparent Data Encryption, TDE) verschlüsselt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-, [!INCLUDE[ssSDSFull](../../../includes/sssdsfull-md.md)]- und [!INCLUDE[ssSDWfull](../../../includes/sssdwfull-md.md)] -Datendateien, bekannt als „Verschlüsselung ruhender Daten“. Sie können verschiedene Vorsichtsmaßnahmen zum Schützen der Datenbank treffen, z.B. Entwerfen eines sicheren Systems, Verschlüsseln vertraulicher Datenbestände und Erstellen einer Firewall für die Datenbankserver. Im Falle eines Diebstahls physischer Medien (Festplatten, Sicherungsbänder oder Ähnliches) kann eine böswillige Partei die Datenbank jedoch einfach wiederherstellen oder anfügen und die Daten durchsuchen. Eine Lösung dieses Problems besteht darin, die sensiblen Daten in der Datenbank zu verschlüsseln, und den für die Verschlüsselung der Daten verwendeten Schlüssel mit einem Zertifikat zu schützen. Dadurch kann niemand die Daten verwenden, der nicht im Besitz der Schlüssel ist. Diese Art des Schutzes muss jedoch im Voraus geplant werden.  
  
 TDE führt die E/A-Verschlüsselung und -Entschlüsselung der Daten- und Protokolldateien in Echtzeit durch. Die Verschlüsselung verwendet einen Datenbank-Verschlüsselungsschlüssel (DEK), der im Startdatensatz der Datenbank gespeichert wird und während der Wiederherstellung zur Verfügung steht. Der DEK ist ein symmetrischer Schlüssel, der durch ein in der Masterdatenbank des Servers gespeichertes Zertifikat gesichert wird, oder ein asymmetrischer Schlüssel, der von einem EKM-Modul geschützt wird. TDE schützt die "ruhenden" Daten, also die Daten- und die Protokolldateien. Sie entspricht den in vielen Branchen etablierten Gesetzen, Bestimmungen und Richtlinien. Dadurch können Softwareentwickler Daten mithilfe der AES- und 3DES-Verschlüsselungsalgorithmen verschlüsseln, ohne vorhandene Anwendungen ändern zu müssen.  
  
> [!IMPORTANT]
>  TDE stellt keine Verschlüsselung über Kommunikationskanäle bereit. Weitere Informationen zum Verschlüsseln von Daten über Kommunikationskanäle finden Sie unter [Aktivieren von verschlüsselten Verbindungen für die Datenbank-Engine &#40;SQL Server-Konfigurations-Manager&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
> 
>  **Verwandte Themen:**  
> 
>  -   [Transparent Data Encryption mit Azure SQL-Datenbank](../../../relational-databases/security/encryption/transparent-data-encryption-azure-sql.md)  
> -   [Erste Schritte mit transparenter Datenverschlüsselung (TDE) in SQL Data Warehouse](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-encryption-tde-tsql/)  
> -   [Verschieben einer TDE-geschützten Datenbank auf einen anderen SQL-Server](../../../relational-databases/security/encryption/move-a-tde-protected-database-to-another-sql-server.md)  
> -   [Aktivieren von TDE in SQL Server mithilfe von EKM](../../../relational-databases/security/encryption/enable-tde-on-sql-server-using-ekm.md)   
> -   [Verwenden von SQL Server-Connector mit SQL-Verschlüsselungsfunktionen](../../../relational-databases/security/encryption/use-sql-server-connector-with-sql-encryption-features.md)
> - [SQL Server Security Blog on TDE with FAQ (SQL Server Blog zu Sicherheitsthemen über TDE mit FAQ)](https://blogs.msdn.microsoft.com/sqlsecurity/2016/10/05/feature-spotlight-transparent-data-encryption-tde/)
 
  
## <a name="about-tde"></a>Informationen zu TDE  
 Die Verschlüsselung der Datenbankdatei erfolgt auf Seitenebene. In einer verschlüsselten Datenbank werden die Seiten verschlüsselt, bevor Sie auf den Datenträger geschrieben werden, und entschlüsselt, wenn sie in den Arbeitsspeicher gelesen werden. TDE erhöht nicht die Größe einer verschlüsselten Datenbank.  
  
 **Informationen zu [!INCLUDE[ssSDS](../../../includes/sssds-md.md)]**  
  
 Bei der Verwendung von TDE mit [!INCLUDE[sqldbesa](../../../includes/sqldbesa-md.md)] V12 wird das auf Serverebene in der „master“-Datenbank gespeicherte Zertifikat automatisch von [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] erstellt. Beim Verschieben einer TDE-Datenbank nach [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] muss die Datenbank für den Verschiebevorgang nicht entschlüsselt werden. Weitere Informationen zur Verwendung von TDE mit [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] finden Sie unter [Transparent Data Encryption with Azure SQL Database (Transparent Data Encryption mit Azure SQL-Datenbank)](../../../relational-databases/security/encryption/transparent-data-encryption-azure-sql.md).  
  
 **Informationen zu [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]**  
  
 Nachdem sie gesichert wurde, kann die Datenbank mit dem richtigen Zertifikat wiederhergestellt werden. Weitere Informationen zu Zertifikaten finden Sie unter [SQL Server Certificates and Asymmetric Keys](../../../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md).  
  
 Wenn Sie TDE aktivieren, sollten Sie das Zertifikat und den privaten Schlüssel, der dem Zertifikat zugeordnet ist, unmittelbar danach sichern. Sollte das Zertifikat einmal nicht mehr verfügbar sein, oder sollten Sie die Datenbank auf einem anderen Server wiederherstellen oder anfügen müssen, müssen Sie über Sicherungen sowohl des Zertifikats als auch des privaten Schlüssels verfügen, da Sie andernfalls die Datenbank nicht öffnen können. Das zum Verschlüsseln verwendete Zertifikat sollte beibehalten werden, selbst wenn TDE für die Datenbank nicht mehr aktiviert ist. Selbst wenn die Datenbank nicht verschlüsselt ist, können Teile des Transaktionsprotokolls nach wie vor geschützt sein. Für bestimmte Vorgänge wird das Zertifikat ggf. weiterhin benötigt, bis eine vollständige Sicherung der Datenbank ausgeführt wurde. Ein abgelaufenes Zertifikat kann immer noch verwendet werden, um Daten mit TDE zu verschlüsseln und zu entschlüsseln.  
  
 **Verschlüsselungshierarchie**  
  
 Die folgende Abbildung zeigt die Architektur der TDE-Verschlüsselung. Nur die Datenbankebenenelemente (der Datenbankverschlüsselungsschlüssel und die ALTER DATABASE-Teile können vom Benutzer bei der Verwendung von TDE in [!INCLUDE[ssSDS](../../../includes/sssds-md.md)]konfiguriert werden.  
  
 ![Zeigt die im Thema beschriebene Hierarchie an](../../../relational-databases/security/encryption/media/tde-architecture.png "Zeigt die im Thema beschriebene Hierarchie an")  
  
## <a name="using-transparent-data-encryption"></a>Verwenden der transparenten Datenverschlüsselung  
 Führen Sie folgende Schritte aus, um TDE zu verwenden:  
  
**Gilt für**: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Erstellen Sie einen Hauptschlüssel  
  
-   Erstellen oder beziehen Sie ein vom Hauptschlüssel geschütztes Zertifikat  
  
-   Erstellen Sie einen Verschlüsselungsschlüssel für die Datenbank, und schützen Sie ihn durch das Zertifikat  
  
-   Legen Sie fest, dass für die Datenbank Verschlüsselung verwendet wird  
  
 Im folgenden Beispiel wird die Verschlüsselung und Entschlüsselung der `AdventureWorks2012` -Datenbank gezeigt, wobei ein auf dem Server `MyServerCert`installiertes Zertifikat verwendet wird.  
  
```sql  
USE master;  
GO  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<UseStrongPasswordHere>';  
go  
CREATE CERTIFICATE MyServerCert WITH SUBJECT = 'My DEK Certificate';  
go  
USE AdventureWorks2012;  
GO  
CREATE DATABASE ENCRYPTION KEY  
WITH ALGORITHM = AES_128  
ENCRYPTION BY SERVER CERTIFICATE MyServerCert;  
GO  
ALTER DATABASE AdventureWorks2012  
SET ENCRYPTION ON;  
GO  
```  
  
 Die Verschlüsselungs- und Entschlüsselungsvorgänge werden in von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]geplanten Hintergrundthreads ausgeführt. Sie können den Status dieser Vorgänge mithilfe der in der Liste weiter unten in diesem Thema genannten Katalogsichten und dynamischen Verwaltungssichten anzeigen.  
  
> [!CAUTION]  
>  Sicherungsdateien von Datenbanken, für die TDE aktiviert wurde, werden ebenfalls mithilfe des Verschlüsselungsschlüssels für die Datenbank verschlüsselt. Darum muss bei der Wiederherstellung dieser Sicherungen das Zertifikat, das zum Verschlüsseln des Verschlüsselungsschlüssels für die Datenbank verwendet wurde, verfügbar sein. Dies bedeutet, dass Sie zusätzlich zur Sicherung der Datenbank auch Sicherungskopien der Serverzertifikate aufbewahren müssen, um einem Datenverlust vorzubeugen. Ist das Zertifikat nicht mehr verfügbar, kann es zu einem Datenverlust kommen. Weitere Informationen finden Sie unter [SQL Server Certificates and Asymmetric Keys](../../../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md).  
  
## <a name="commands-and-functions"></a>Befehle und Funktionen  
 Die für TDE verwendeten Zertifikate müssen mithilfe des Datenbank-Hauptschlüssels verschlüsselt sein, damit sie von den folgenden Anweisungen akzeptiert werden. Eine Verschlüsselung nur durch ein Kennwort lehnen die Anweisungen ab.  
  
> [!IMPORTANT]  
>  Wenn die Zertifikate nach der Verwendung durch TDE mit einem Kennwortschutz versehen werden, kann auf die Datenbank nach einem Neustart nicht mehr zugegriffen werden.  
  
 Die folgende Tabelle bietet Links und Erläuterungen zu den Befehlen und Funktionen von TDE.  
  
|Befehl oder Funktion|Zweck|  
|-------------------------|-------------|  
|[CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/create-database-encryption-key-transact-sql.md)|Erstellt einen Schlüssel, der verwendet wird, um eine Datenbank zu verschlüsseln.|  
|[ALTER DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-database-encryption-key-transact-sql.md)|Ändert den Schlüssel, der verwendet wird, um eine Datenbank zu verschlüsseln.|  
|[DROP DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/drop-database-encryption-key-transact-sql.md)|Entfernt den Schlüssel, der verwendet wurde, um eine Datenbank zu verschlüsseln.|  
|[ALTER DATABASE SET-Optionen &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-database-transact-sql-set-options.md)|Erklärt die **ALTER DATABASE** -Option, mit der TDE aktiviert wird.|  
  
## <a name="catalog-views-and-dynamic-management-views"></a>Katalogsichten und dynamische Verwaltungssichten  
 In der folgenden Tabelle werden die Katalogsichten und die dynamischen Verwaltungssichten von TDE erläutert.  
  
|Katalogsicht oder dynamische Verwaltungssicht|Zweck|  
|---------------------------------------------|-------------|  
|[sys.databases &#40;Transact-SQL&#41;](../../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)|Katalogsicht, die Datenbankinformationen anzeigt.|  
|[sys.certificates &#40;Transact-SQL&#41;](../../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)|Katalogsicht, die die Zertifikate in einer Datenbank anzeigt.|  
|[sys.dm_database_encryption_keys &#40;Transact-SQL&#41;](../../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md)|Dynamische Verwaltungssicht, die Informationen zu den in einer Datenbank verwendeten Verschlüsselungsschlüsseln und dem aktuellen Status der Verschlüsselung einer Datenbank bereitstellt.|  
  
## <a name="permissions"></a>Berechtigungen  
 Jede Funktion und jeder Befehl von TDE erfordert bestimmte Berechtigungen, die in den zuvor gezeigten Tabellen beschrieben wurden.  
  
 Um die in Beziehung zu TDE stehenden Metadaten anzuzeigen, ist die VIEW DEFINITION-Berechtigung für das Zertifikat erforderlich.  
  
## <a name="considerations"></a>Überlegungen  
 Während eine erneute Verschlüsselungsprüfung für einen Datenbankverschlüsselungsvorgang ausgeführt wird, sind Wartungsvorgänge für die Datenbank deaktiviert. Sie können den Einzelbenutzermodus für die Datenbank verwenden, um einen Wartungsvorgang durchzuführen. Weitere Informationen finden Sie unter [So legen Sie den Einzelbenutzermodus für eine Datenbank fest](../../../relational-databases/databases/set-a-database-to-single-user-mode.md).  
  
 Der Verschlüsselungsstatus der Datenbank wird mit der dynamischen Verwaltungssicht sys.dm_database_encryption_keys angezeigt. Weitere Informationen finden Sie im Abschnitt „Katalogsichten und dynamische Verwaltungssichten“ weiter oben in diesem Thema.  
  
 Bei TDE werden alle Dateien und Dateigruppen in der Datenbank verschlüsselt. Wenn Dateigruppen in einer Datenbank als READ ONLY markiert sind, schlägt der Datenbankverschlüsselungsvorgang fehl.  
  
 Wenn eine Datenbank bei Datenbankspiegelung oder Protokollversand verwendet wird, werden beide Datenbanken verschlüsselt. Die Protokolltransaktionen werden für die Übertragung zwischen den Datenbanken verschlüsselt.  
  
> [!IMPORTANT]  
>  Volltextindizes werden verschlüsselt, wenn für eine Datenbank die Verschlüsselung festgelegt ist. Vor SQL Server 2008 erstellte Volltextindizes werden während des Upgrades auf SQL Server 2008 oder höher in die Datenbank importiert, und sie werden durch TDE verschlüsselt.  

> [!TIP]  
> Verwenden Sie SQL Server Audit oder SQL-Datenbanküberwachung, um die Veränderungen im TDE-Status einer Datenbank zu überwachen. Bei SQL Server wird TDE unter der Überwachungsaktionsgruppe DATABASE_CHANGE_GROUP nachverfolgt, die in [SQL Server Audit-Aktionsgruppen und -Aktionen](../../../relational-databases/security/auditing/sql-server-audit-action-groups-and-actions.md) enthalten ist.
  
### <a name="restrictions"></a>Beschränkungen  
 Die folgende Vorgänge sind während der ersten Datenbankverschlüsselung, einer Schlüsseländerung oder der Datenbankentschlüsselung nicht erlaubt:  
  
-   Löschen einer Datei aus einer Dateigruppe in der Datenbank  
  
-   Löschen der Datenbank  
  
-   Offlineschalten der Datenbank  
  
-   Trennen einer Datenbank  
  
-   Versetzen einer Datenbank oder einer Dateigruppe in den READ ONLY-Zustand  
  
 Die folgenden Vorgänge sind während der Ausführung der Anweisungen CREATE DATABASE ENCRYPTION KEY, ALTER DATABASE ENCRYPTION KEY, DROP DATABASE ENCRYPTION KEY oder ALTER DATABASE...SET ENCRYPTION nicht erlaubt:  
  
-   Löschen einer Datei aus einer Dateigruppe in der Datenbank.  
  
-   Löschen der Datenbank.  
  
-   Offlineschalten der Datenbank.  
  
-   Trennen einer Datenbank.  
  
-   Versetzen einer Datenbank oder einer Dateigruppe in den READ ONLY-Zustand.  
  
-   Verwenden eines ALTER DATABASE-Befehls.  
  
-   Starten einer Datenbank- oder Datenbankdateisicherung.  
  
-   Starten einer Datenbank- oder Datenbankdateiwiederherstellung.  
  
-   Erstellen einer Momentaufnahme.  
  
 Die folgenden Vorgänge oder Bedingungen verhindern die Anweisungen CREATE DATABASE ENCRYPTION KEY, ALTER DATABASE ENCRYPTION KEY, DROP DATABASE ENCRYPTION KEY oder ALTER DATABASE...SET ENCRYPTION.  
  
-   Die Datenbank ist schreibgeschützt oder hat schreibgeschützte Dateigruppen.  
  
-   Ein ALTER DATABASE-Befehl wird ausgeführt.  
  
-   Eine Datensicherung wird ausgeführt.  
  
-   Die Datenbank ist offline geschaltet oder wird wiederhergestellt.  
  
-   Eine Momentaufnahme wird ausgeführt.  
  
-   Datenbankwartungstasks  
  
 Beim Erstellen von Datenbankdateien ist die sofortige Dateiinitialisierung nicht verfügbar, wenn TDE aktiviert ist.  
  
 Um den Verschlüsselungsschlüssel für die Datenbank mit einem asymmetrischen Schlüssel zu verschlüsseln, muss sich der asymmetrische Schlüssel auf einem erweiterbaren Schlüsselverwaltungsanbieter befinden.  
  
### <a name="transparent-data-encryption-and-transaction-logs"></a>Transparente Datenverschlüsselung und Transaktionsprotokolle  
 Die Aktivierung einer Datenbank für die Verwendung von TDE führt dazu, dass der verbleibende Teil des virtuellen Transaktionsprotokolls auf 0 festgelegt wird. Dadurch wird ein neues virtuelles Transaktionsprotokoll erzwungen. Dies gewährleistet, dass in den Transaktionsprotokollen kein Klartext verbleibt, nachdem die Datenbank für die Verschlüsselung eingerichtet wurde. Sie können den Status der Protokolldateiverschlüsselung erkennen, wenn Sie die `encryption_state`-Spalte in der `sys.dm_database_encryption_keys`-Sicht anzeigen, wie in diesem Beispiel:  
  
```  
USE AdventureWorks2012;  
GO  
/* The value 3 represents an encrypted state   
   on the database and transaction logs. */  
SELECT *  
FROM sys.dm_database_encryption_keys  
WHERE encryption_state = 3;  
GO  
```  
  
 Weitere Informationen zur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Protokolldateiarchitektur finden Sie unter [Das Transaktionsprotokoll &#40;SQL Server&#41;](../../../relational-databases/logs/the-transaction-log-sql-server.md).  
  
 Alle vor einer Änderung des Datenbank-Verschlüsselungsschlüssels in das Transaktionsprotokoll geschriebenen Daten werden mithilfe des vorherigen Verschlüsselungsschlüssels für die Datenbank verschlüsselt.  
  
 Nachdem ein Verschlüsselungsschlüssel für die Datenbank zweimal geändert wurde, muss eine Protokollsicherung ausgeführt werden, bevor der Verschlüsselungsschlüssel für die Datenbank wieder geändert werden kann.  
  
### <a name="transparent-data-encryption-and-the-tempdb-system-database"></a>Transparente Datenverschlüsselung und die tempdb-Systemdatenbank  
 Die tempdb-Systemdatenbank wird verschlüsselt, wenn eine beliebige andere Datenbank in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanz mithilfe von TDE verschlüsselt ist. Dies könnte sich auf die Leistung unverschlüsselter Datenbanken der gleichen Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]auswirken. Weitere Informationen über die tempdb-Systemdatenbank finden Sie unter [tempdb-Datenbank](../../../relational-databases/databases/tempdb-database.md).  
  
### <a name="transparent-data-encryption-and-replication"></a>Transparente Datenverschlüsselung und Replikation  
 Daten aus einer TDE-aktivierten Datenbank werden bei der Replikation nicht automatisch in einer verschlüsselten Form repliziert. Sie müssen TDE separat aktivieren, wenn Sie die Verteilungs- und Abonnentendatenbanken schützen möchten. Bei der Snapshotreplikation sowie bei der ursprünglichen Verteilung von Daten für die Transaktions- und Mergereplikation können Daten in unverschlüsselten Zwischendateien gespeichert werden – dies sind z. B. die BCP-Dateien.  Während der Transaktions- oder Mergereplikation kann die Verschlüsselung aktiviert werden, um den Kommunikationskanal zu schützen. Weitere Informationen finden Sie unter [Aktivieren von verschlüsselten Verbindungen zur Datenbank-Engine &#40;SQL Server-Konfigurations-Manager&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
### <a name="transparent-data-encryption-and-filestream-data"></a>Transparente Datenverschlüsselung und FILESTREAM-Daten  
 FILESTREAM-Daten werden nicht verschlüsselt, auch dann nicht, wenn TDE aktiviert ist.  

<a name="scan-suspend-resume"></a>

## <a name="transparent-data-encryption-tde-scan"></a>TDE-Überprüfung (Transparent Data Encryption)

Damit Transparent Data Encryption (TDE) für eine Datenbank aktiviert werden kann, muss [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] eine Verschlüsselungsüberprüfung durchführen, bei der alle Seiten aus den Datendateien in den Pufferpool gelesen und die verschlüsselten Seiten dann auf den Datenträger geschrieben werden. Mit [!INCLUDE[sql-server-2019](../../../includes/sssqlv15-md.md)] wurde die Syntax für das Anhalten und Fortsetzen des TDE-Scans eingeführt, mit der Sie den Scan während unternehmenskritischen Zeiten oder hoher Auslastung des Systems anhalten und später fortsetzen können, damit Benutzer über mehr Kontrolle über den Verschlüsselungsscan verfügen.

Verwenden Sie die folgende Syntax, um den TDE-Verschlüsselungsscan anzuhalten:

```sql
ALTER DATABASE <db_name> SET ENCRYPTION SUSPEND;
```

Auf ähnliche Weise können Sie den TDE-Verschlüsselungsscan mithilfe der folgenden Syntax fortsetzen:

```sql
ALTER DATABASE <db_name> SET ENCRYPTION RESUME;
```

`encryption_scan_state` wurde der dynamischen Verwaltungssicht `sys.dm_database_encryption_keys` hinzugefügt, um den aktuellen Status des Verschlüsselungsscans anzuzeigen. Außerdem wurde eine neue Spalte namens `encryption_scan_modify_date` hinzugefügt, die das Datum und die Uhrzeit der letzten Änderung des Status des Verschlüsselungsscans enthält. Beachten Sie außerdem, dass beim Start eine Meldung im Fehlerprotokoll protokolliert wird, die angibt, dass ein vorhandener Scan pausiert wurde, wenn die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz neu gestartet wird, während die Verschlüsselungsüberprüfung angehalten ist.
  
## <a name="transparent-data-encryption-and-buffer-pool-extension"></a>Transparente Datenverschlüsselung und Pufferpoolerweiterung  
 Dateien, die mit der Pufferpoolerweiterung (BPE, Buffer Pool Extension) zusammenhängen, werden bei der Verschlüsselung der Datenbank mit TDE nicht verschlüsselt. Für mit BPE zusammenhängende Dateien müssen Sie Verschlüsselungstools auf Dateisystemebene verwenden, z. B. Bitlocker oder EFS.  
  
## <a name="transparent-data-encryption-and-in-memory-oltp"></a>Transparente Datenverschlüsselung und In-Memory OLTP  
 TDE kann auf einer Datenbank aktiviert werden, die über In-Memory OLTP-Objekte verfügt. In [!INCLUDE[ssSQL15](../../../includes/sssql15-md.md)] und [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] werden In-Memory OLTP-Protokolldatensätze und Daten verschlüsselt, wenn TDE aktiviert ist. In [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] werden In-Memory OLTP-Protokolldatensätze verschlüsselt, wenn TDE aktiviert ist, aber Dateien in der MEMORY_OPTIMIZED_DATA-Dateigruppe werden nicht verschlüsselt.  
  
## <a name="related-tasks"></a>Related Tasks  
 [Verschieben einer TDE-geschützten Datenbank auf einen anderen SQL-Server](../../../relational-databases/security/encryption/move-a-tde-protected-database-to-another-sql-server.md)  
 [Aktivieren von TDE in SQL Server mithilfe von EKM](../../../relational-databases/security/encryption/enable-tde-on-sql-server-using-ekm.md)  
 [Erweiterbare Schlüsselverwaltung mit Azure Key Vault &#40;SQL Server&#41;](../../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [Transparent Data Encryption mit Azure SQL-Datenbank](../../../relational-databases/security/encryption/transparent-data-encryption-azure-sql.md)  
 [Erste Schritte mit transparenter Datenverschlüsselung (TDE) in SQL Data Warehouse](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-encryption-tde-tsql/)  
 [SQL Server-Verschlüsselung](../../../relational-databases/security/encryption/sql-server-encryption.md)  
 [Verschlüsselungsschlüssel für SQL Server und Datenbank &#40;Datenbank-Engine&#41;](../../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)  
   
## <a name="see-also"></a>Weitere Informationen  
 [Sicherheitscenter für SQL Server-Datenbank-Engine und Azure SQL-Datenbank](../../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)   
 [FILESTREAM &#40;SQL Server&#41;](../../../relational-databases/blob/filestream-sql-server.md)  
  
  
