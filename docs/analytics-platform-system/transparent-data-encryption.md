---
title: Transparent Data Encryption
description: Die transparente Datenverschlüsselung (TDE) für parallele Data Warehouse (PDW) führt die e/a-Verschlüsselung und-Entschlüsselung der Daten-und Transaktionsprotokoll Dateien und der speziellen PDW-Protokolldateien in Echtzeit durch. "
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: dc6b582895a684386ed2d14b0c31612dcd0a47d1
ms.sourcegitcommit: 370cab80fba17c15fb0bceed9f80cb099017e000
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2020
ms.locfileid: "97641566"
---
# <a name="transparent-data-encryption"></a>Transparente Datenverschlüsselung
Sie können verschiedene Vorsichtsmaßnahmen zum Schützen der Datenbank treffen, z.B. Entwerfen eines sicheren Systems, Verschlüsseln vertraulicher Datenbestände und Erstellen einer Firewall für die Datenbankserver. In einem Szenario, in dem die physischen Medien (z. b. Laufwerke oder Sicherungsbänder) gestohlen werden, kann eine böswillige Partei jedoch die Datenbank einfach wiederherstellen oder Anfügen und die Daten durchsuchen. Eine Lösung dieses Problems besteht darin, die sensiblen Daten in der Datenbank zu verschlüsseln, und den für die Verschlüsselung der Daten verwendeten Schlüssel mit einem Zertifikat zu schützen. Dadurch kann niemand die Daten verwenden, der nicht im Besitz der Schlüssel ist. Diese Art des Schutzes muss jedoch im Voraus geplant werden.  
  
*Transparent Data Encryption* (TDE) führt die e/a-Verschlüsselung und-Entschlüsselung der Daten-und Transaktionsprotokoll Dateien und der speziellen PDW-Protokolldateien in Echtzeit durch. Die Verschlüsselung verwendet einen Datenbank-Verschlüsselungsschlüssel (DEK), der im Startdatensatz der Datenbank gespeichert wird und während der Wiederherstellung zur Verfügung steht. Der DEK ist ein symmetrischer Schlüssel, der durch ein in der Master-Datenbank des SQL Server PDW gespeichertes Zertifikat gesichert wird. TDE schützt die "ruhenden" Daten, also die Daten- und die Protokolldateien. Sie entspricht den in vielen Branchen etablierten Gesetzen, Bestimmungen und Richtlinien. Mit dieser Funktion können Softwareentwickler Daten mithilfe von AES-und 3DES-Verschlüsselungsalgorithmen verschlüsseln, ohne vorhandene Anwendungen ändern zu müssen.  
  
> [!IMPORTANT]  
> TDE stellt keine Verschlüsselung für Daten bereit, die zwischen dem Client und dem PDW übertragen werden. Weitere Informationen zum Verschlüsseln von Daten zwischen dem Client und SQL Server PDW finden Sie unter [Bereitstellen eines Zertifikats](provision-certificate.md).  
>   
> TDE verschlüsselt Daten nicht, während Sie verschoben oder verwendet werden. Interner Datenverkehr zwischen den PDW-Komponenten innerhalb des SQL Server PDW wird nicht verschlüsselt. Die temporär in Speicher Puffern gespeicherten Daten werden nicht verschlüsselt. Um dieses Risiko zu mindern, kontrollieren Sie den physischen Zugriff und die Verbindungen mit dem SQL Server PDW.  
  
Nachdem sie gesichert wurde, kann die Datenbank mit dem richtigen Zertifikat wiederhergestellt werden.  
  
> [!NOTE]  
> Wenn Sie ein Zertifikat für TDE erstellen, sollten Sie es zusammen mit dem zugehörigen privaten Schlüssel sofort sichern. Sollte das Zertifikat einmal nicht mehr verfügbar sein, oder sollten Sie die Datenbank auf einem anderen Server wiederherstellen oder anfügen müssen, müssen Sie über Sicherungen sowohl des Zertifikats als auch des privaten Schlüssels verfügen, da Sie andernfalls die Datenbank nicht öffnen können. Das zum Verschlüsseln verwendete Zertifikat sollte beibehalten werden, selbst wenn TDE für die Datenbank nicht mehr aktiviert ist. Selbst wenn die Datenbank nicht verschlüsselt ist, können Teile des Transaktionsprotokolls nach wie vor geschützt sein. Für bestimmte Vorgänge wird das Zertifikat ggf. weiterhin benötigt, bis eine vollständige Sicherung der Datenbank ausgeführt wurde. Ein abgelaufenes Zertifikat kann immer noch verwendet werden, um Daten mit TDE zu verschlüsseln und zu entschlüsseln.  
  
Die Verschlüsselung der Datenbankdatei erfolgt auf Seitenebene. In einer verschlüsselten Datenbank werden die Seiten verschlüsselt, bevor Sie auf den Datenträger geschrieben werden, und entschlüsselt, wenn sie in den Arbeitsspeicher gelesen werden. TDE erhöht nicht die Größe einer verschlüsselten Datenbank.  
  
Die folgende Abbildung zeigt die Schlüssel Hierarchie für die TDE-Verschlüsselung:  
  
![Zeigt die Hierarchie an](media/tde-architecture.png "TDE_Architecture")  
  
## <a name="using-transparent-data-encryption"></a><a name="using-tde"></a>Verwenden der transparenten Datenverschlüsselung  
Führen Sie folgende Schritte aus, um TDE zu verwenden: Die ersten drei Schritte werden nur einmal ausgeführt, wenn Sie SQL Server PDW für die Unterstützung von TDE vorbereiten.  
  
1.  Erstellen Sie einen Hauptschlüssel in der Master-Datenbank.  
  
2.  Verwenden Sie **sp_pdw_database_encryption** , um TDE auf dem SQL Server PDW zu aktivieren. Durch diesen Vorgang werden die temporären Datenbanken geändert, um den Schutz zukünftiger temporärer Daten sicherzustellen, und es tritt ein Fehler auf, wenn aktive Sitzungen vorhanden sind, die temporäre Tabellen aufweisen. **sp_pdw_database_encryption** die die Maskierung von Benutzerdaten in PDW-Systemprotokollen einschaltet. (Weitere Informationen zur Maskierung von Benutzerdaten in PDW-Systemprotokollen finden Sie unter [sp_pdw_log_user_data_masking](../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md).)  
  
3.  Verwenden Sie [sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md) , um Anmelde Informationen zu erstellen, die sich authentifizieren und in die Freigabe schreiben können, in der die Sicherung des Zertifikats gespeichert wird. Wenn für den vorgesehenen Speicherserver bereits Anmelde Informationen vorhanden sind, können Sie die vorhandenen Anmelde Informationen verwenden.  
  
4.  Erstellen Sie in der Master-Datenbank ein Zertifikat, das durch den Hauptschlüssel geschützt ist.  
  
5.  Sichern Sie das Zertifikat in der Speicherfreigabe.  
  
6.  Erstellen Sie in der Benutzerdatenbank einen Verschlüsselungsschlüssel für die Datenbank, und schützen Sie ihn durch das Zertifikat, das in der Master-Datenbank gespeichert ist.  
  
7.  Verwenden Sie die- `ALTER DATABASE` Anweisung, um die Datenbank mithilfe von TDE zu verschlüsseln.  
  
Das folgende Beispiel veranschaulicht das Verschlüsseln der- `AdventureWorksPDW2012` Datenbank mithilfe eines Zertifikats namens `MyServerCert` , das in SQL Server PDW erstellt wurde.  
  
**Zuerst: Aktivieren Sie TDE für die SQL Server PDW.** Diese Aktion ist nur einmal erforderlich.  
  
```sql  
USE master;  
GO  
  
-- Create a database master key in the master database  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<UseStrongPasswordHere>';  
GO  
  
-- Enable encryption for PDW  
EXEC sp_pdw_database_encryption 1;  
GO  
  
-- Add a credential that can write to the share  
-- A credential created for a backup can be used if you wish  
EXEC sp_pdw_add_network_credentials 'SECURE_SERVER', '<domain>\<Windows_user>', '<password>';  
```  
  
**Zweitens: Erstellen und sichern Sie ein Zertifikat in der Master-Datenbank.** Diese Aktion ist nur einmal erforderlich. Sie können über ein separates Zertifikat für jede Datenbank verfügen (empfohlen), oder Sie können mehrere Datenbanken mit einem Zertifikat schützen.  
  
```sql  
-- Create certificate in master  
CREATE CERTIFICATE MyServerCert WITH SUBJECT = 'My DEK Certificate';  
GO  
  
-- Back up the certificate with private key  
BACKUP CERTIFICATE MyServerCert   
    TO FILE = '\\SECURE_SERVER\cert\MyServerCert.cer'  
    WITH PRIVATE KEY   
    (   
        FILE = '\\SECURE_SERVER\cert\MyServerCert.key',  
        ENCRYPTION BY PASSWORD = '<UseStrongPasswordHere>'   
    )   
GO  
```  
  
**Zuletzt: Erstellen Sie den DEK, und verwenden Sie ALTER DATABASE, um eine Benutzerdatenbank zu verschlüsseln.** Diese Aktion wird für jede Datenbank wiederholt, die durch TDE geschützt wird.  
  
```sql  
USE AdventureWorksPDW2012;  
GO  
  
CREATE DATABASE ENCRYPTION KEY  
WITH ALGORITHM = AES_128  
ENCRYPTION BY SERVER CERTIFICATE MyServerCert;  
GO  
  
ALTER DATABASE AdventureWorksPDW2012 SET ENCRYPTION ON;  
GO  
```  
  
Die Verschlüsselungs- und Entschlüsselungsvorgänge werden von SQL Server in geplanten Hintergrundthreads ausgeführt. Sie können den Status dieser Vorgänge mithilfe der Katalog Sichten und dynamischen Verwaltungs Sichten in der Liste anzeigen, die später in diesem Artikel angezeigt wird.  
  
> [!CAUTION]  
> Sicherungsdateien von Datenbanken, für die TDE aktiviert wurde, werden ebenfalls mithilfe des Verschlüsselungsschlüssels für die Datenbank verschlüsselt. Darum muss bei der Wiederherstellung dieser Sicherungen das Zertifikat, das zum Verschlüsseln des Verschlüsselungsschlüssels für die Datenbank verwendet wurde, verfügbar sein. Dies bedeutet, dass Sie zusätzlich zur Sicherung der Datenbank auch Sicherungskopien der Serverzertifikate aufbewahren müssen, um einem Datenverlust vorzubeugen. Ist das Zertifikat nicht mehr verfügbar, kann es zu einem Datenverlust kommen.  
  
## <a name="commands-and-functions"></a>Befehle und Funktionen  
Die für TDE verwendeten Zertifikate müssen mithilfe des Datenbank-Hauptschlüssels verschlüsselt sein, damit sie von den folgenden Anweisungen akzeptiert werden.  
  
Die folgende Tabelle bietet Links und Erläuterungen zu den Befehlen und Funktionen von TDE.  
  
|Befehl oder Funktion|Zweck|  
|-----------------------|-----------|  
|[CREATE DATABASE ENCRYPTION KEY](../t-sql/statements/create-database-encryption-key-transact-sql.md)|Erstellt einen Schlüssel, der verwendet wird, um eine Datenbank zu verschlüsseln.|  
|[ALTER DATABASE ENCRYPTION KEY](../t-sql/statements/alter-database-encryption-key-transact-sql.md)|Ändert den Schlüssel, der verwendet wird, um eine Datenbank zu verschlüsseln.|  
|[DROP DATABASE ENCRYPTION KEY](../t-sql/statements/drop-database-encryption-key-transact-sql.md)|Entfernt den Schlüssel, der verwendet wurde, um eine Datenbank zu verschlüsseln.|  
|[ALTER DATABASE](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw)|Erläutert die **ALTER DATABASE** -Option, die verwendet wird, um TDE zu aktivieren.|  
  
## <a name="catalog-views-and-dynamic-management-views"></a>Katalogsichten und dynamische Verwaltungssichten  
In der folgenden Tabelle werden die Katalogsichten und die dynamischen Verwaltungssichten von TDE erläutert.  
  
|Katalogsicht oder dynamische Verwaltungssicht|Zweck|  
|-------------------------------------------|-----------|  
|[sys.databases](../relational-databases/system-catalog-views/sys-databases-transact-sql.md)|Katalogsicht, die Datenbankinformationen anzeigt.|  
|[sys.certificates](../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)|Katalogsicht, die die Zertifikate in einer Datenbank anzeigt.|  
|[sys.dm_pdw_nodes_database_encryption_keys](../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-database-encryption-keys-transact-sql.md)|Dynamische Verwaltungs Sicht, die Informationen für jeden Knoten, Informationen zu den in einer Datenbank verwendeten Verschlüsselungsschlüsseln und den Verschlüsselungs Status einer Datenbank bereitstellt.|  
  
## <a name="permissions"></a>Berechtigungen  
Jede Funktion und jeder Befehl von TDE erfordert bestimmte Berechtigungen, die in den zuvor gezeigten Tabellen beschrieben wurden.  
  
Zum Anzeigen der an TDE beteiligten Metadaten ist die- `CONTROL SERVER` Berechtigung erforderlich.  
  
## <a name="considerations"></a>Überlegungen  
Während eine erneute Verschlüsselungsprüfung für einen Datenbankverschlüsselungsvorgang ausgeführt wird, sind Wartungsvorgänge für die Datenbank deaktiviert.  
  
Sie können den Status der Datenbankverschlüsselung mithilfe der dynamischen Verwaltungs Sicht **sys.dm_pdw_nodes_database_encryption_keys** ermitteln. Weitere Informationen finden Sie weiter oben in diesem Artikel im Abschnitt *Katalog Sichten und dynamische Verwaltungs Sichten* .  
  
### <a name="restrictions"></a>Beschränkungen  
Die folgenden Vorgänge sind während der-,-,-oder-Anweisungen nicht zulässig `CREATE DATABASE ENCRYPTION KEY` `ALTER DATABASE ENCRYPTION KEY` `DROP DATABASE ENCRYPTION KEY` `ALTER DATABASE...SET ENCRYPTION` .  
  
-   Löschen der Datenbank.  
  
-   Mit einem `ALTER DATABASE` Befehl.  
  
-   Starten einer Datenbanksicherung.  
  
-   Eine Daten Bank Wiederherstellung wird gestartet.  
  
Die folgenden Vorgänge oder Bedingungen verhindern die-,-,- `CREATE DATABASE ENCRYPTION KEY` `ALTER DATABASE ENCRYPTION KEY` oder- `DROP DATABASE ENCRYPTION KEY` `ALTER DATABASE...SET ENCRYPTION` Anweisungen.  
  
-   Ein `ALTER DATABASE` Befehl wird ausgeführt.  
  
-   Eine Datensicherung wird ausgeführt.  
  
Beim Erstellen von Datenbankdateien ist die sofortige Dateiinitialisierung nicht verfügbar, wenn TDE aktiviert ist.  
  
### <a name="areas-not-protected-by-tde"></a>Bereiche, die nicht durch TDE geschützt sind  
TDE schützt keine externen Tabellen.  
  
TDE schützt keine Diagnose Sitzungen. Benutzer sollten darauf achten, dass Sie keine Abfragen mit sensiblen Parametern ausführen, während Diagnose Sitzungen verwendet werden. Diagnose Sitzungen, die vertrauliche Informationen offenlegen, sollten gelöscht werden, sobald Sie nicht mehr benötigt werden.  
  
Die von TDE geschützten Daten werden entschlüsselt, wenn Sie in SQL Server PDW Arbeitsspeicher eingefügt werden. Speicher Abbilder werden erstellt, wenn bestimmte Probleme auf dem Gerät auftreten. Dumpdateien stellen den Inhalt des Arbeitsspeichers zum Zeitpunkt der Problem Darstellung dar und können vertrauliche Daten in unverschlüsselter Form enthalten. Der Inhalt der Speicher Abbilder sollte überprüft werden, bevor Sie für andere Benutzer freigegeben werden.  
  
Die Master-Datenbank wird nicht durch TDE geschützt. Obwohl die Master-Datenbank keine Benutzerdaten enthält, enthält Sie Informationen, wie z. b. Anmelde Namen.  
  
### <a name="transparent-data-encryption-and-transaction-logs"></a>Transparente Datenverschlüsselung und Transaktionsprotokolle  
Wenn eine Datenbank für die Verwendung von TDE aktiviert wird, hat dies den Effekt, dass der verbleibende Teil des virtuellen Transaktions Protokolls zerrochen wird, um das nächste virtuelle Transaktionsprotokoll zu erzwingen. Dies gewährleistet, dass in den Transaktionsprotokollen kein Klartext verbleibt, nachdem die Datenbank für die Verschlüsselung eingerichtet wurde. Sie können den Status der Protokolldatei Verschlüsselung auf jedem PDW-Knoten ermitteln, indem Sie die- `encryption_state` Spalte in der- `sys.dm_pdw_nodes_database_encryption_keys` Sicht anzeigen, wie in diesem Beispiel gezeigt:  
  
```sql  
WITH dek_encryption_state AS   
(  
    SELECT ISNULL(db_map.database_id, dek.database_id) AS database_id, encryption_state  
    FROM sys.dm_pdw_nodes_database_encryption_keys AS dek  
        INNER JOIN sys.pdw_nodes_pdw_physical_databases AS node_db_map  
           ON dek.database_id = node_db_map.database_id AND dek.pdw_node_id = node_db_map.pdw_node_id  
        LEFT JOIN sys.pdw_database_mappings AS db_map  
            ON node_db_map .physical_name = db_map.physical_name  
        INNER JOIN sys.dm_pdw_nodes AS nodes  
            ON nodes.pdw_node_id = dek.pdw_node_id  
    WHERE dek.encryptor_thumbprint <> 0x  
)  
SELECT TOP 1 encryption_state  
       FROM dek_encryption_state  
       WHERE dek_encryption_state.database_id = DB_ID('AdventureWorksPDW2012 ')  
       ORDER BY (CASE encryption_state WHEN 3 THEN -1 ELSE encryption_state END) DESC;  
```  
  
Alle vor einer Änderung des Datenbank-Verschlüsselungsschlüssels in das Transaktionsprotokoll geschriebenen Daten werden mithilfe des vorherigen Verschlüsselungsschlüssels für die Datenbank verschlüsselt.  
  
### <a name="pdw-activity-logs"></a>PDW-Aktivitäts Protokolle  
SQL Server PDW verwaltet eine Reihe von Protokollen, die für die Problembehandlung vorgesehen sind. (Beachten Sie, dass es sich nicht um das Transaktionsprotokoll, das SQL Server Fehlerprotokoll oder das Windows-Ereignisprotokoll handelt.) Diese PDW-Aktivitäts Protokolle können vollständige Anweisungen enthalten, die einige Benutzerdaten enthalten können. Typische Beispiele sind **Insert** -und **Update** -Anweisungen. Die Maskierung von Benutzerdaten kann mithilfe von **sp_pdw_log_user_data_masking** explizit aktiviert oder deaktiviert werden. Durch Aktivieren der Verschlüsselung auf SQL Server PDW wird die Maskierung von Benutzerdaten in PDW-Aktivitäts Protokollen automatisch aktiviert, um Sie zu schützen. **sp_pdw_log_user_data_masking** können auch verwendet werden, um-Anweisungen zu maskieren, wenn TDE nicht verwendet wird, dies wird jedoch nicht empfohlen, da das Microsoft-Support Team die Möglichkeiten der Analyse von Problemen erheblich reduziert.  
  
### <a name="transparent-data-encryption-and-the-tempdb-system-database"></a>Transparente Datenverschlüsselung und die tempdb-Systemdatenbank  
Die tempdb-Systemdatenbank wird verschlüsselt, wenn die Verschlüsselung mithilfe von [sp_pdw_database_encryption](../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)aktiviert wird. Dies ist erforderlich, bevor TDE von einer Datenbank verwendet werden kann. Dies kann sich auf die Leistung unverschlüsselter Datenbanken in derselben Instanz von SQL Server PDW auswirken.  
  
## <a name="key-management"></a>Schlüsselverwaltung  
Der Datenbank-Verschlüsselungsschlüssel (Database Encryption Key, DEK) wird durch die in der Master-Datenbank gespeicherten Zertifikate geschützt. Diese Zertifikate werden durch den Datenbank-Hauptschlüssel (Database Master Key, DMK) der Master-Datenbank geschützt. Die DMK muss durch den Dienst Hauptschlüssel (Service Master Key, SMK) geschützt werden, um für TDE verwendet werden zu können.  
  
Das System kann auf die Schlüssel zugreifen, ohne dass ein Benutzereingriff erforderlich ist (z. b. ein Kennwort). Wenn das Zertifikat nicht verfügbar ist, gibt das System einen Fehler aus, der erklärt, dass der DEK nicht entschlüsselt werden kann, bis das richtige Zertifikat verfügbar ist.  
  
Wenn eine Datenbank von einem Gerät in ein anderes verschoben wird, muss das Zertifikat, das zum Schutz seiner DEK verwendet wird, zuerst auf dem Zielserver wieder hergestellt werden. Anschließend kann die Datenbank wie gewohnt wieder hergestellt werden. Weitere Informationen finden Sie in der Standard SQL Server-Dokumentation unter [Verschieben einer TDE-geschützten Datenbank in eine andere SQL Server](../relational-databases/security/encryption/move-a-tde-protected-database-to-another-sql-server.md).  
  
Zertifikate, die zum Verschlüsseln von-Zertifikaten verwendet werden, sollten beibehalten werden, solange Sie Datenbanksicherungen verwenden, die Sie verwenden. Zertifikat Sicherungen müssen den privaten Schlüssel des Zertifikats enthalten, da ein Zertifikat ohne den privaten Schlüssel nicht für die Daten Bank Wiederherstellung verwendet werden kann. Die Sicherungen des privaten Zertifikat Schlüssels werden in einer separaten Datei gespeichert, die durch ein Kennwort geschützt ist, das für die Zertifikat Wiederherstellung bereitgestellt werden muss.  
  
## <a name="restoring-the-master-database"></a>Wiederherstellen der master-Datenbank  
Die Master-Datenbank kann mithilfe von **dwconfig** als Teil der Notfall Wiederherstellung wieder hergestellt werden.  
  
-   Wenn sich der Steuer Knoten nicht geändert hat, d. h., wenn die Master-Datenbank auf demselben und unveränderten Gerät wieder hergestellt wird, von dem aus die Sicherung der Master-Datenbank erstellt wurde, sind die DMK und alle Zertifikate ohne zusätzliche Maßnahmen lesbar.  
  
-   Wenn die Master-Datenbank auf einer anderen Appliance wieder hergestellt wird oder der Steuerungs Knoten seit der Sicherung der Master-Datenbank geändert wurde, müssen zusätzliche Schritte ausgeführt werden, um die Datenbank neu zu generieren.  
  
    1.  Öffnen Sie die DMK:  
  
        ```sql  
        OPEN MASTER KEY DECRYPTION BY PASSWORD = '<password>';  
        ```  
  
    2.  Fügen Sie die Verschlüsselung nach SMK hinzu:  
  
        ```sql  
        ALTER MASTER KEY   
            ADD ENCRYPTION BY SERVICE MASTER KEY;  
        ```  
  
    3.  Starten Sie das Gerät neu.  
  
## <a name="upgrade-and-replacing-virtual-machines"></a>Aktualisieren und ersetzen Virtual Machines  
Wenn auf dem Gerät, auf dem ein Upgrade oder eine Replace-VM ausgeführt wurde, ein DMK vorhanden ist, muss das DMK-Kennwort als Parameter angegeben werden.  
  
Beispiel für die Upgradeaktion. Ersetzen `**********` Sie durch ihr DMK-Kennwort.  
  
`setup.exe /Action=ProvisionUpgrade ... DMKPassword='**********'`  
  
Beispiel für die Aktion zum Ersetzen einer virtuellen Maschine.  
  
`setup.exe /Action=ReplaceVM ... DMKPassword='**********'`  
  
Wenn beim Upgrade eine Benutzer-DB verschlüsselt ist und das DMK-Kennwort nicht angegeben wird, tritt bei der Upgradeaktion ein Fehler auf. Wenn während des Ersetzens kein gültiges Kennwort angegeben wird, wenn ein DMK vorhanden ist, überspringt der Vorgang den Wiederherstellungs Schritt von DMK. Alle anderen Schritte werden am Ende der Aktion "VM ersetzen" abgeschlossen, aber die Aktion meldet einen Fehler am Ende, um anzugeben, dass zusätzliche Schritte erforderlich sind. In den Setup Protokollen (befindet sich unter **\programdata\microsoft\microsoft SQL Server parallel Data Warehouse-\100\logs\setup \\<Zeitstempel> \detail-Setup**), wird am Ende die folgende Warnung angezeigt.  
  
`**_ WARNING \_\*\* DMK is detected in master database, but could not be recovered automatically! The DMK password was either not provided or is incorrect!`
  
Führen Sie diese Anweisung in PDW manuell aus, und starten Sie die Anwendung anschließend neu, um DMK wiederherzustellen:  
  
```sql
OPEN MASTER KEY DECRYPTION BY PASSWORD = '<DMK password>';  
ALTER MASTER KEY ADD ENCRYPTION BY SERVICE MASTER KEY;  
```
  
Führen Sie die Schritte im Abschnitt **Wiederherstellen der Master-Datenbank** aus, um die Datenbank wiederherzustellen, und starten Sie das Gerät neu.  
  
Wenn die Datenbank bereits vorhanden war, aber nach der Aktion nicht wieder hergestellt wurde, wird die folgende Fehlermeldung ausgelöst, wenn eine Datenbank abgefragt wird.  
  
```sql
Msg 110806;  
A distributed query failed: Database '<db_name>' cannot be opened due to inaccessible files or insufficient memory or disk space. See the SQL Server errorlog for details.
```  
  
## <a name="performance-impact"></a>Leistungsauswirkungen  
Die Auswirkungen von TDE auf die Leistung variieren abhängig von der Art der Daten, der Art der Speicherung und der Art der Arbeits Auslastungs Aktivität auf der SQL Server PDW. Beim Schutz durch TDE ist die e/a-Vorgänge zum Lesen und anschließenden Entschlüsseln von Daten oder zum Verschlüsseln und anschließenden Schreiben von Daten eine CPU-intensive Aktivität und hat mehr Auswirkungen, wenn gleichzeitig andere CPU-intensive Aktivitäten durchgeführt werden. TDE verschlüsselt `tempdb` , kann TDE sich auf die Leistung von Datenbanken auswirken, die nicht verschlüsselt sind. Um eine genaue Vorstellung der Leistung zu erhalten, sollten Sie das gesamte System mit Ihrer Daten-und Abfrage Aktivität testen.  
  
## <a name="related-content"></a>Verwandte Inhalte  
Die folgenden Links enthalten allgemeine Informationen darüber, wie SQL Server die Verschlüsselung verwaltet. Diese Artikel helfen Ihnen, die SQL Server Verschlüsselung zu verstehen, aber diese Artikel enthalten keine Informationen, die für SQL Server PDW spezifisch sind, und Sie erörtern Features, die nicht in SQL Server PDW vorhanden sind.  
  
-   [SQL Server-Verschlüsselung](../relational-databases/security/encryption/sql-server-encryption.md)  
  
-   [Verschlüsselungshierarchie](../relational-databases/security/encryption/encryption-hierarchy.md)  
  
-   [Verschlüsselungsschlüssel für SQL Server und Datenbank](../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)  

  
## <a name="see-also"></a>Weitere Informationen  
[ALTER DATABASE](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw)  
[CREATE MASTER KEY](../t-sql/statements/create-master-key-transact-sql.md)  
[CREATE DATABASE ENCRYPTION KEY](../t-sql/statements/create-database-encryption-key-transact-sql.md)  
[BACKUP CERTIFICATE](../t-sql/statements/backup-certificate-transact-sql.md)  
[sp_pdw_database_encryption](../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)  
[sp_pdw_database_encryption_regenerate_system_keys](../relational-databases/system-stored-procedures/sp-pdw-database-encryption-regenerate-system-keys-sql-data-warehouse.md)  
[sp_pdw_log_user_data_masking](../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md)  
[sys.certificates](../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)  
[sys.dm_pdw_nodes_database_encryption_keys](../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-database-encryption-keys-transact-sql.md)  
