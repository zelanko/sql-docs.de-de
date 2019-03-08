---
title: Transparente datenverschlüsselung – Parallel Data Warehouse | Microsoft-Dokumentation
description: Transparente datenverschlüsselung (TDE) für Parallel Data Warehouse (PDW) führt eine e/a-Verschlüsselung und-Entschlüsselung der Daten und Transaktionsprotokolldateien und die speziellen PDW-Protokolldateien."
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: e9067416365e56dccf9c09f2e826c01fb3ecfa3c
ms.sourcegitcommit: 8bc5d85bd157f9cfd52245d23062d150b76066ef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/07/2019
ms.locfileid: "57578490"
---
# <a name="transparent-data-encryption"></a>Transparente Datenverschlüsselung
Sie können verschiedene Vorsichtsmaßnahmen treffen, um eine Datenbank abzusichern, beispielsweise ein sicheres System entwerfen, vertrauliche Datenbestände verschlüsseln oder eine Firewall für die Datenbankserver einrichten. Allerdings für ein Szenario, in dem die physischen Medien (z. B. Festplatten oder Sicherungsbänder) gestohlen werden, kann eine böswillige Partei nur wiederherstellen oder Anfügen der Datenbank und die Daten durchsuchen. Eine Lösung dieses Problems besteht darin, die sensiblen Daten in der Datenbank zu verschlüsseln, und den für die Verschlüsselung der Daten verwendeten Schlüssel mit einem Zertifikat zu schützen. Dadurch kann niemand die Daten verwenden, der nicht im Besitz der Schlüssel ist. Diese Art des Schutzes muss jedoch im Voraus geplant werden.  
  
*Transparente datenverschlüsselung* (TDE) führt eine e/a-Verschlüsselung und-Entschlüsselung der Daten und Transaktionsprotokolldateien und den speziellen PDW-Protokolldateien. Die Verschlüsselung verwendet einen Verschlüsselungsschlüssel für die Datenbank (Database Encryption Key, DEK), der in der Datenbankstartseite gespeichert wird, damit er während der Wiederherstellung verfügbar ist. Der DEK ist ein symmetrischer Schlüssel, die gesichert werden, mithilfe eines Zertifikats in der master-Datenbank von SQL Server-PDW gespeichert. TDE schützt die "ruhenden" Daten, also die Daten- und die Protokolldateien. Sie entspricht den in vielen Branchen etablierten Gesetzen, Bestimmungen und Richtlinien. Dadurch können Softwareentwickler Daten mithilfe von AES und 3DES Verschlüsselungsalgorithmen ohne Änderung vorhandener Anwendungen verschlüsseln.  
  
> [!IMPORTANT]  
> TDE stellt keine Verschlüsselung für Daten, die zwischen dem Client und dem PDW zurücklegen bereit. Weitere Informationen zum Verschlüsseln von Daten zwischen dem Client und der SQL Server PDW finden Sie unter [Bereitstellen eines Zertifikats](provision-certificate.md).  
>   
> TDE werden Daten nicht verschlüsselt, beim Verschieben oder verwendet. Interner Datenverkehr zwischen PDW-Komponenten in der SQL Server PDW werden nicht verschlüsselt. Daten, die temporär im Arbeitsspeicher gespeichert werden nicht verschlüsselt. Um dieses Risiko zu verringern, können steuern Sie physischen Zugriff und Verbindungen mit SQL Server-PDW.  
  
Nachdem sie gesichert wurde, kann die Datenbank mit dem richtigen Zertifikat wiederhergestellt werden.  
  
> [!NOTE]  
> Wenn Sie ein Zertifikat für TDE erstellen, sollten Sie sofort es, zusammen mit den zugehörigen privaten Schlüssel sichern. Sollte das Zertifikat einmal nicht mehr verfügbar sein, oder sollten Sie die Datenbank auf einem anderen Server wiederherstellen oder anfügen müssen, müssen Sie über Sicherungen sowohl des Zertifikats als auch des privaten Schlüssels verfügen, da Sie andernfalls die Datenbank nicht öffnen können. Das zum Verschlüsseln verwendete Zertifikat sollte beibehalten werden, selbst wenn TDE für die Datenbank nicht mehr aktiviert ist. Selbst wenn die Datenbank nicht verschlüsselt ist, können Teile des Transaktionsprotokolls nach wie vor geschützt sein. Für bestimmte Vorgänge wird das Zertifikat ggf. weiterhin benötigt, bis eine vollständige Sicherung der Datenbank ausgeführt wurde. Ein abgelaufenes Zertifikat kann immer noch verwendet werden, um Daten mit TDE zu verschlüsseln und zu entschlüsseln.  
  
Die Verschlüsselung der Datenbankdatei wird auf Seitenebene ausgeführt. In einer verschlüsselten Datenbank werden die Seiten verschlüsselt, bevor Sie auf den Datenträger geschrieben werden, und entschlüsselt, wenn sie in den Arbeitsspeicher gelesen werden. TDE erhöht nicht die Größe einer verschlüsselten Datenbank.  
  
Die folgende Abbildung zeigt die Hierarchie der Schlüssel für TDE-Verschlüsselung:  
  
![Zeigt die Hierarchie](media/tde-architecture.png "TDE_Architecture")  
  
## <a name="using-tde"></a>Verwenden die transparente datenverschlüsselung  
Führen Sie folgende Schritte aus, um TDE zu verwenden: Die ersten drei Schritte sind nur einmal durchgeführt werden, bei der Vorbereitung von SQL Server PDW um TDE zu unterstützen.  
  
1.  Erstellen Sie einen Hauptschlüssel in der master-Datenbank ein.  
  
2.  Verwendung **sp_pdw_database_encryption aktiviert werden** So aktivieren Sie TDE für die SQL Server PDW. Dieser Vorgang ändert die temporären Datenbanken, um sicherzustellen, dass den Schutz der zukünftigen temporäre Daten und schlägt fehl, wenn versucht wird, wenn aktive Sitzungen, die temporäre Tabellen vorhanden sind. **sp_pdw_database_encryption aktiviert werden** Benutzer datenmaskierung in Systemprotokollen PDW aktiviert. (Weitere Informationen zum Benutzer datenmaskierung in PDW-Systemprotokolle, finden Sie unter [Sp_pdw_log_user_data_masking](../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md).)  
  
3.  Verwendung [Sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md) , Anmeldeinformationen zu erstellen, können zu authentifizieren, und Schreiben in die Dateifreigabe, in dem die Sicherung des Zertifikats gespeichert werden kann wird. Wenn die Anmeldeinformationen für den gewünschten Server bereits vorhanden ist, können Sie die vorhandene Anmeldeinformationen verwenden.  
  
4.  Erstellen Sie in der master-Datenbank ein Zertifikat mit dem Hauptschlüssel geschützt.  
  
5.  Sichern Sie das Zertifikat in die Storage-Freigabe.  
  
6.  Erstellen Sie in der Benutzerdatenbank einen Verschlüsselungsschlüssel für Datenbank, und schützen Sie, indem Sie das Zertifikat, das in der master-Datenbank gespeichert ist.  
  
7.  Verwenden der `ALTER DATABASE` Anweisung, um die Datenbank mithilfe von TDE zu verschlüsseln.  
  
Das folgende Beispiel veranschaulicht das Verschlüsseln der `AdventureWorksPDW2012` -Datenbank mithilfe eines Zertifikats namens `MyServerCert`, der in SQL Server PDW.  
  
**Zuerst: Aktivieren von TDE in SQLServer PDW.** Diese Aktion ist nur einmal erforderlich.  
  
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
  
**Sekunde: Erstellen Sie und Sichern Sie ein Zertifikat in der master-Datenbank.** Diese Aktion ist nur einmal erforderlich. Sie können ein separates Zertifikat für jede Datenbank (empfohlen), oder Sie können mehrere Datenbanken mit einem einzelnen Zertifikat schützen.  
  
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
  
**Die letzten: Erstellen Sie den DEK und verwenden Sie ALTER DATABASE, um eine Benutzerdatenbank zu verschlüsseln.** Diese Aktion wird für jede Datenbank wiederholt, die TDE-Schutz ist.  
  
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
  
Die Ver- und Entschlüsselung-Vorgänge werden von SQL Server in Hintergrundthreads geplant. Sie können anzeigen, dass den Status dieser Vorgänge mithilfe der Katalogsichten und dynamische Verwaltungssichten in der Liste, die später in diesem Artikel wird angezeigt.  
  
> [!CAUTION]  
> Sicherungsdateien von Datenbanken, für die TDE aktiviert wurde, werden ebenfalls mithilfe des Verschlüsselungsschlüssels für die Datenbank verschlüsselt. Darum muss bei der Wiederherstellung dieser Sicherungen das Zertifikat, das zum Verschlüsseln des Verschlüsselungsschlüssels für die Datenbank verwendet wurde, verfügbar sein. Dies bedeutet, dass Sie zusätzlich zur Sicherung der Datenbank auch Sicherungskopien der Serverzertifikate aufbewahren müssen, um einem Datenverlust vorzubeugen. Ist das Zertifikat nicht mehr verfügbar, kann es zu einem Datenverlust kommen.  
  
## <a name="commands-and-functions"></a>Befehle und Funktionen  
Die für TDE verwendeten Zertifikate müssen mithilfe des Datenbank-Hauptschlüssels verschlüsselt sein, damit sie von den folgenden Anweisungen akzeptiert werden.  
  
Die folgende Tabelle bietet Links und Erläuterungen zu den Befehlen und Funktionen von TDE.  
  
|Befehl oder Funktion|Zweck|  
|-----------------------|-----------|  
|[VERSCHLÜSSELUNGSSCHLÜSSEL FÜR DATENBANK ERSTELLEN](../t-sql/statements/create-database-encryption-key-transact-sql.md)|Erstellt einen Schlüssel, der verwendet wird, um eine Datenbank zu verschlüsseln.|  
|[ALTER DATABASE ENCRYPTION KEY](../t-sql/statements/alter-database-encryption-key-transact-sql.md)|Ändert den Schlüssel, der verwendet wird, um eine Datenbank zu verschlüsseln.|  
|[DROP DATABASE ENCRYPTION KEY](../t-sql/statements/drop-database-encryption-key-transact-sql.md)|Entfernt den Schlüssel, der verwendet wurde, um eine Datenbank zu verschlüsseln.|  
|[ALTER DATABASE](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw)|Erklärt die **ALTER DATABASE** -Option, mit der TDE aktiviert wird.|  
  
## <a name="catalog-views-and-dynamic-management-views"></a>Katalogsichten und dynamische Verwaltungssichten  
In der folgenden Tabelle werden die Katalogsichten und die dynamischen Verwaltungssichten von TDE erläutert.  
  
|Katalogsicht oder dynamische Verwaltungssicht|Zweck|  
|-------------------------------------------|-----------|  
|[sys.databases](../relational-databases/system-catalog-views/sys-databases-transact-sql.md)|Katalogsicht, die Datenbankinformationen anzeigt.|  
|[sys.certificates](../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)|Katalogsicht, die die Zertifikate in einer Datenbank anzeigt.|  
|[sys.dm_pdw_nodes_database_encryption_keys](../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-database-encryption-keys-transact-sql.md)|Dynamische verwaltungssicht, die Informationen für jeden Knoten in einer Datenbank, und der Status der Verschlüsselung einer Datenbank verwendeten Verschlüsselungsschlüssel bereitstellt.|  
  
## <a name="permissions"></a>Berechtigungen  
Jede Funktion und jeder Befehl von TDE erfordert bestimmte Berechtigungen, die in den zuvor gezeigten Tabellen beschrieben wurden.  
  
Anzeigen von Metadaten in Beziehung zu TDE erfordert die `CONTROL SERVER` Berechtigung.  
  
## <a name="considerations"></a>Weitere Überlegungen  
Während eine erneute Verschlüsselungsprüfung für einen Datenbankverschlüsselungsvorgang ausgeführt wird, sind Wartungsvorgänge für die Datenbank deaktiviert.  
  
Sie finden den Status der Verschlüsselung für die Datenbank mithilfe der **sys.dm_pdw_nodes_database_encryption_keys** dynamische verwaltungssicht. Weitere Informationen finden Sie unter den *Katalogsichten und dynamische Verwaltungssichten* weiter oben in diesem Artikel.  
  
### <a name="restrictions"></a>Restrictions  
Die folgenden Vorgänge sind nicht zulässig, während die `CREATE DATABASE ENCRYPTION KEY`, `ALTER DATABASE ENCRYPTION KEY`, `DROP DATABASE ENCRYPTION KEY`, oder `ALTER DATABASE...SET ENCRYPTION` Anweisungen.  
  
-   Löschen der Datenbank.  
  
-   Verwenden einer `ALTER DATABASE` Befehl.  
  
-   Eine datenbanksicherung wird gestartet.  
  
-   Starten Sie eine Wiederherstellung der Datenbank.  
  
Die folgenden Vorgänge oder Bedingungen werden verhindert, dass die `CREATE DATABASE ENCRYPTION KEY`, `ALTER DATABASE ENCRYPTION KEY`, `DROP DATABASE ENCRYPTION KEY`, oder `ALTER DATABASE...SET ENCRYPTION` Anweisungen.  
  
-   Ein `ALTER DATABASE` Befehl ausgeführt wird.  
  
-   Eine Datensicherung wird ausgeführt.  
  
Beim Erstellen von Datenbankdateien ist die sofortige Dateiinitialisierung nicht verfügbar, wenn TDE aktiviert ist.  
  
### <a name="areas-not-protected-by-tde"></a>Bereiche, die nicht durch TDE geschützte  
TDE schützt die externe Tabellen nicht.  
  
TDE schützt nicht diagnosesitzungen. Benutzer sollten vorsichtig sein, nicht zu Abfragen mit sensiblen Parametern während diagnosesitzungen verwendet werden. Diagnosesitzungen, die sensiblen Informationen preisgeben dürfen gelöscht werden, sobald sie nicht mehr benötigt werden.  
  
Durch TDE geschützte Daten werden entschlüsselt, wenn im SQL Server-PDW-Arbeitsspeicher platziert. Speicherabbilder werden erstellt, wenn bestimmte Probleme, auf dem Gerät auftreten. Sichern Sie Dateien stellen den Inhalt des Arbeitsspeichers zum Zeitpunkt des Auftretens Problem, und kann vertrauliche Daten in unverschlüsselter Form enthalten. Der Inhalt des Speicherabbilder sollte überprüft werden, bevor sie für andere Benutzer freigegeben werden.  
  
Die master-Datenbank ist nicht mit TDE geschützt. Obwohl der master-Datenbank keine Benutzerdaten enthält, enthält es Informationen wie z. B. Anmeldenamen.  
  
### <a name="transparent-data-encryption-and-transaction-logs"></a>Transparente Datenverschlüsselung und Transaktionsprotokolle  
Aktivieren einer Datenbank mit TDE hat den Effekt unwiderrufliche des verbleibenden Teils des virtuellen Transaktionsprotokolls auf den nächsten virtuelles Transaktionsprotokoll erzwungen. Dies gewährleistet, dass in den Transaktionsprotokollen kein Klartext verbleibt, nachdem die Datenbank für die Verschlüsselung eingerichtet wurde. Sie finden den Status der Verschlüsselung der Log-Datei auf jedem Knoten PDW anhand der `encryption_state` -Spalte in der `sys.dm_pdw_nodes_database_encryption_keys` anzeigen, wie im folgenden Beispiel:  
  
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
  
### <a name="pdw-activity-logs"></a>PDW-Aktivitätsprotokolle  
SQL Server PDW verwaltet einen Satz von Protokollen, die für die Problembehandlung vorgesehen. (Beachten Sie, dass nicht das Transaktionsprotokoll, das SQL Server-Fehlerprotokoll oder im Windows-Ereignisprotokoll.) Diese PDW-Aktivitätsprotokolle können vollständige Anweisungen in Klartext enthalten, von die einige Benutzerdaten enthalten kann. Typische Beispiele sind **einfügen** und **UPDATE** Anweisungen. Maskieren von Daten des Benutzers kann werden explizit aktiviert oder deaktiviert mit **Sp_pdw_log_user_data_masking**. Aktivieren der Verschlüsselung auf SQL Server PDW automatisch aktiviert das Maskieren von Benutzerdaten in PDW-Aktivitätsprotokollen um sie zu schützen. **Sp_pdw_log_user_data_masking** kann auch verwendet werden, um Anweisungen zu maskieren, ohne Verwendung von TDE, wird jedoch nicht empfohlen, da es die Fähigkeit der Microsoft-Support-Team, Analysieren von Problemen erheblich reduziert wird.  
  
### <a name="transparent-data-encryption-and-the-tempdb-system-database"></a>Transparente Datenverschlüsselung und die tempdb-Systemdatenbank  
Die Tempdb-Systemdatenbank wird verschlüsselt, bei aktivierter Verschlüsselung mit [sp_pdw_database_encryption aktiviert werden](../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md). Dies ist erforderlich, bevor eine beliebige Datenbank TDE verwenden kann. Dies kann eine Auswirkung auf die Leistung unverschlüsselter Datenbanken auf derselben Instanz von SQL Server PDW haben.  
  
## <a name="key-management"></a>Schlüsselverwaltung  
Die Datenbank-Verschlüsselungsschlüssels (DEK) ist durch die Zertifikate, die in der master-Datenbank gespeicherten geschützt. Diese Zertifikate werden mit dem Datenbank-Hauptschlüssel (Datenbank-Hauptschlüssel) der master-Datenbank geschützt. Datenbank-Hauptschlüssels muss durch den Diensthauptschlüssel (SMK) geschützt werden, um für TDE verwendet werden.  
  
Das System kann die Schlüssel zugreifen, ohne dass menschliches Eingreifen erforderlich (z. B. die Angabe eines Kennworts). Wenn das Zertifikat nicht verfügbar ist, gibt das System einen Fehler mit der Meldung, dass es sich bei der DEK nicht entschlüsselt werden kann, bis das richtige Zertifikat verfügbar ist.  
  
Beim Verschieben einer Datenbank von einer Appliance in ein anderes, das Zertifikat zum Schützen der "DEK muss zuerst auf dem Zielserver wiederhergestellt werden. Klicken Sie dann kann die Datenbank wie gewohnt wiederhergestellt werden. Weitere Informationen finden Sie in der standardmäßigen SQL Server-Dokumentation unter [Verschieben einer TDE-geschützten Datenbank auf einen anderen SQL Server](https://technet.microsoft.com/library/ff773063.aspx).  
  
Zertifikate, die zum Verschlüsseln des DEKs sollte beibehalten werden, solange es datenbanksicherungen, die diese verwenden. Sicherungen des Zertifikats müssen dem privaten Schlüssel des Zertifikats enthalten, da ohne den privaten Schlüssel ein Zertifikats für die Wiederherstellung der Datenbank verwendet werden kann. Dieser private Schlüssel der Sicherung von Zertifikaten werden in einer separaten Datei gespeichert, geschützt durch ein Kennwort, die für die Zertifikat-Wiederherstellung bereitgestellt werden müssen.  
  
## <a name="restoring-the-master-database"></a>Wiederherstellen der master-Datenbank  
Die master-Datenbank kann wiederhergestellt werden, mithilfe von **DWConfig**, im Rahmen der Wiederherstellung im Notfall.  
  
-   Wenn es sich bei der Steuerelementknoten aus nicht geändert hat, ist das Wenn der master-Datenbank auf dem gleichen und unverändert Gerät wiederhergestellt wird, von dem die Sicherung der Masterdatenbank erstellt wurde, der Datenbank-Hauptschlüssel und alle Zertifikate lesbar, ohne dass weitere Aktionen werden.  
  
-   Wenn der master-Datenbank auf einem anderen Gerät wiederhergestellt wird oder wenn der steuerknoten seit der Sicherung der master-Datenbank geändert wurde, werden zusätzliche Schritte erforderlich sein, um der Datenbank-Hauptschlüssel neu generieren.  
  
    1.  Öffnen Sie die Datenbank-Hauptschlüssel:  
  
        ```sql  
        OPEN MASTER KEY DECRYPTION BY PASSWORD = '<password>';  
        ```  
  
    2.  Fügen Sie die Verschlüsselung von SMK hinzu:  
  
        ```sql  
        ALTER MASTER KEY   
            ADD ENCRYPTION BY SERVICE MASTER KEY;  
        ```  
  
    3.  Starten Sie das Gerät neu.  
  
## <a name="upgrade-and-replacing-virtual-machines"></a>Upgrade und Ersetzen von virtuellen Computern  
Wenn ein Datenbank-Hauptschlüssel auf dem Gerät vorhanden ist, auf dem Upgrade oder ersetzen-VM ausgeführt wurde, muss die Datenbank-Hauptschlüssel Kennwort als Parameter angegeben werden.  
  
Beispiel: der Upgradeaktion. Ersetzen Sie dies `**********` mit Ihrem Kennwort Datenbank-Hauptschlüssel.  
  
`setup.exe /Action=ProvisionUpgrade ... DMKPassword='**********'`  
  
Beispiel für die Aktion, die einen virtuellen Computer zu ersetzen.  
  
`setup.exe /Action=ReplaceVM ... DMKPassword='**********'`  
  
Während des Upgrades fehl, wenn eine Benutzerdatenbank wird verschlüsselt, und das Kennwort des Datenbank-Hauptschlüssel nicht angegeben wird, die Upgradeaktion. Beim Ersetzen Sie dies Wenn das korrekte Kennwort nicht angegeben wird, wenn ein Datenbank-Hauptschlüssel vorhanden ist, wird der Vorgang den Datenbank-Hauptschlüssel Recovery Schritt überspringen. Alle anderen Schritte werden am Ende die Replace-VM-Vorgänge abgeschlossen werden, aber die Aktion Fehler am Ende melden wird, um anzugeben, dass zusätzliche Schritte erforderlich sind. In die Setupprotokolle (befindet sich in **\ProgramData\Microsoft\Microsoft SQL Server Parallel Data Warehouse\100\Logs\Setup\\< Zeitstempel > \Detail-Setup**), die folgende Warnung wird im unteren Bereich angezeigt.  
  
`*** WARNING \*\*\* DMK is detected in master database, but could not be recovered automatically! The DMK password was either not provided or is incorrect!`
  
Führen Sie diese Anweisung manuell in PDW, und starten Sie danach Gerät neu, um die Datenbank-Hauptschlüssel wiederherstellen:  
  
```sql
OPEN MASTER KEY DECRYPTION BY PASSWORD = '<DMK password>';  
ALTER MASTER KEY ADD ENCRYPTION BY SERVICE MASTER KEY;  
```
  
Verwenden Sie die Schritte in der **wiederherstellen den master-Datenbank** Absatz zum Wiederherstellen der Datenbank, und starten Sie das Gerät neu.  
  
Wenn der Datenbank-Hauptschlüssel vorhanden, bevor Sie waren aber nicht nach der Aktion wiederhergestellt wurde, wird die folgende Fehlermeldung wird ausgelöst, wenn eine Datenbank abgefragt wird.  
  
```sql
Msg 110806;  
A distributed query failed: Database '<db_name>' cannot be opened due to inaccessible files or insufficient memory or disk space. See the SQL Server errorlog for details.
```  
  
## <a name="performance-impact"></a>Leistungsauswirkungen  
Die Auswirkungen auf die Leistung von TDE variiert mit dem Typ der Daten, was man, wie sie gespeichert sind und den Typ der Workload-Aktivität in der SQL Server PDW. Wenn TDE-Schutz, wird die e/a von lesen und Entschlüsseln von Daten oder die Verschlüsselung und klicken Sie dann das Schreiben von Daten ist eine intensive CPU-Aktivität und hat mehrere Auswirkungen, wenn andere CPU-intensiven Aktivitäten zur gleichen Zeit ausgeführt werden. Da TDE verschlüsselt `tempdb`, TDE kann beeinträchtigen die Leistung von Datenbanken, die nicht verschlüsselt werden. Um eine genaue Vorstellung der Leistung zu erhalten, sollten Sie das gesamte System mit Ihrer Aktivität Daten und Abfragen testen.  
  
## <a name="related-content"></a>Verwandte Inhalte  
Die folgenden Links enthalten allgemeine Informationen dazu, wie Verschlüsselung von SQL Server verwaltet. Diese Artikel helfen zu verstehen, SQL Server-Verschlüsselung, aber dieser Artikel keine Informationen zu SQL Server PDW sie diskutieren, Funktionen, die in SQL Server PDW nicht vorhanden sind.  
  
-   [SQL Server-Verschlüsselung](../relational-databases/security/encryption/sql-server-encryption.md)  
  
-   [Verschlüsselungshierarchie](../relational-databases/security/encryption/encryption-hierarchy.md)  
  
-   [Verschlüsselungsschlüssel für SQL Server und Datenbank](../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)  

  
## <a name="see-also"></a>Siehe auch  
[ALTER DATABASE](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw)  
[CREATE MASTER KEY](../t-sql/statements/create-master-key-transact-sql.md)  
[VERSCHLÜSSELUNGSSCHLÜSSEL FÜR DATENBANK ERSTELLEN](../t-sql/statements/create-database-encryption-key-transact-sql.md)  
[BACKUP CERTIFICATE](../t-sql/statements/backup-certificate-transact-sql.md)  
[sp_pdw_database_encryption](../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)  
[sp_pdw_database_encryption_regenerate_system_keys](../relational-databases/system-stored-procedures/sp-pdw-database-encryption-regenerate-system-keys-sql-data-warehouse.md)  
[sp_pdw_log_user_data_masking](../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md)  
[sys.certificates](../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)  
[sys.dm_pdw_nodes_database_encryption_keys](../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-database-encryption-keys-transact-sql.md)  
  
