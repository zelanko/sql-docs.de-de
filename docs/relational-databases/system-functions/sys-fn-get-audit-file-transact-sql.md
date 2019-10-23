---
title: sys. fn_get_audit_file (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_get_audit_file_TSQL
- sys.fn_get_audit_file_TSQL
- fn_get_audit_file
- sys.fn_get_audit_file
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fn_get_audit_file function
- fn_get_audit_file function
ms.assetid: d6a78d14-bb1f-4987-b7b6-579ddd4167f5
author: rothja
ms.author: jroth
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7fa19a06d3743e91665ee2355eb5f6c380df413d
ms.sourcegitcommit: 8cb26b7dd40280a7403d46ee59a4e57be55ab462
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2019
ms.locfileid: "72542233"
---
# <a name="sysfn_get_audit_file-transact-sql"></a>sys.fn_get_audit_file (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt Informationen von einer Überwachungsdatei zurück, die von einer Serverüberwachung in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellt wurde. Weitere Informationen finden Sie unter [SQL Server Audit &#40;Datenbank-Engine&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  
 ![Themen Link Symbol](../../database-engine/configure-windows/media/topic-link.gif "Link Symbol "Thema"") [Transact-SQL-Syntax Konventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
fn_get_audit_file ( file_pattern,   
    { default | initial_file_name | NULL },   
    { default | audit_record_offset | NULL } )  
```  
  
## <a name="arguments"></a>Argumente  
 *file_pattern*  
 Gibt das Verzeichnis oder den Pfad und den Dateinamen für den zu lesenden Überwachungsdateisatz an. Type ist vom Datentyp **nvarchar (260)** . 
 
 - **SQL Server**:
    
    Dieses Argument muss sowohl einen Pfad (Laufwerksbuchstabe oder Netzwerkfreigabe) als auch einen Dateinamen umfassen. Diese können ein Platzhalterzeichen enthalten. Ein einzelnes Sternchen (*) kann verwendet werden, um mehrere Dateien aus einem Überwachungs Datei Satz zu erfassen. Beispiel:  
  
    -   **\<path > \\ \*** alle Überwachungs Dateien am angegebenen Speicherort sammeln.  
  
    -   **\<path > \LoginsAudit_{GUID}** -alle Überwachungs Dateien mit dem angegebenen Namen und dem angegebenen GUID-paar erfassen.  
  
    -   **\<path>\LoginsAudit_{GUID}_00_29384.sqlaudit** - Collect a specific audit file.  
  
 - **Azure SQL-Datenbank**:
 
    Dieses Argument wird verwendet, um eine BLOB-URL (einschließlich Speicher Endpunkt und Container) anzugeben. Obwohl ein Platzhalter Zeichen nicht unterstützt wird, können Sie ein partielles Dateinamen Präfix (anstelle des vollständigen BLOB-namens) verwenden, um mehrere Dateien (BLOBs) zu sammeln, die mit diesem Präfix beginnen. Beispiel:
 
      - **\<Storage_endpoint \> / \<Container \> / \<ServerName \> / 0DatabaseName 1 2** : sammelt alle Überwachungs Dateien (blobdateien) für die jeweilige Datenbank.    
      
      - **\<Storage_endpoint \> / \<Container \> / \<ServerName \> / 0DatabaseName 1 2 3AuditName 4 5 6CreationDate 7 8 9FileName 0. xel** : sammelt eine bestimmte Überwachungs Datei (BLOB).
  
> [!NOTE]  
>  Einen Pfad ohne ein Dateinamenmuster zu übergeben generiert einen Fehler.  
  
 *initial_file_name*  
 Gibt den Pfad und den Namen einer bestimmten Datei im Überwachungsdateisatz an, von der an die Überwachungsdatensätze gelesen werden sollen. Type ist vom Datentyp **nvarchar (260)** .  
  
> [!NOTE]  
>  Das Argument *initial_file_name* muss gültige Einträge enthalten oder entweder den Standardwert | NULL-Wert.  
  
 *audit_record_offset*  
 Gibt einen bekannten Speicherort mit der für initial_file_name angegebenen Datei an. Wenn dieses Argument verwendet wird, beginnt die Funktion mit dem Lesen beim ersten Datensatz des Puffers, der direkt nach dem festgelegten Offset folgt.  
  
> [!NOTE]  
>  Das Argument *audit_record_offset* muss gültige Einträge enthalten oder entweder den Standardwert | NULL-Wert. Der Typ ist " **bigint**".  
  
## <a name="tables-returned"></a>Zurückgegebene Tabellen  
 In der folgenden Tabelle wird der Inhalt der Überwachungsdatei beschrieben, die von dieser Funktion zurückgegeben werden kann.  
  
| Spaltenname | Geben Sie | Description |  
|-------------|------|-------------|  
| action_id | **varchar(4)** | ID der Aktion. Lässt keine NULL-Werte zu. |  
| additional_information | **nvarchar(4000)** | Eindeutige Informationen, die nur für ein einzelnes Ereignis gelten, werden als XML zurückgegeben. Eine kleine Anzahl überwachbarer Aktionen enthält diese Art von Informationen.<br /><br /> Eine Ebene des TSQL-Stapels wird im XML-Format für Aktionen angezeigt, denen ein TSQL-Stapel zugeordnet ist. Das XML-Format sieht folgendermaßen aus:<br /><br /> `<tsql_stack><frame nest_level = '%u' database_name = '%.*s' schema_name = '%.*s' object_name = '%.*s' /></tsql_stack>`<br /><br /> Frame nest_level gibt die aktuelle Schachtelungsebene des Frames an. Der Modulname (database_name, schema_name und object_name) wird in einem aus drei Teilen bestehenden Format dargestellt.  Der Modulname wird so analysiert, dass ungültige XML-Zeichen wie `'\<'`, `'>'` `'/'`, `'_x'` mit Escapezeichen versehen werden. Sie werden als `_xHHHH\_` mit Escapezeichen versehen. HHHH steht für den vierstelligen hexadezimalen UCS 2-Code für das Zeichen<br /><br /> Lässt NULL-Werte zu. Gibt NULL zurück, wenn keine zusätzlichen vom Ereignis gemeldeten Informationen vorliegen. |
| affected_rows | **bigint** | **Gilt für**: nur Azure SQL-DB<br /><br /> Anzahl der von der ausgeführten Anweisung betroffenen Zeilen. |  
| application_name | **nvarchar(128)** | **Gilt für**: Azure SQL-DB + SQL Server (beginnend mit 2017)<br /><br /> Der Name der Client Anwendung, die die Anweisung ausgeführt hat, die das Überwachungs Ereignis verursacht hat. |  
| audit_file_offset | **bigint** | **Gilt für**: nur SQL Server<br /><br /> Der Pufferoffset in der Datei, die den Überwachungsdatensatz enthält. Lässt keine NULL-Werte zu. |  
| audit_schema_version | **int** | Immer 1 |  
| class_type | **varchar(2)** | Der Typ der überwachbaren Entität, bei der die Überwachung auftritt. Lässt keine NULL-Werte zu. |  
| client_ip | **nvarchar(128)** | **Gilt für**: Azure SQL-DB + SQL Server (beginnend mit 2017)<br /><br />    Quell-IP der Client Anwendung |  
| connection_id | GUID | **Gilt für**: Azure SQL-Datenbank und verwaltete Instanz<br /><br /> Die ID der Verbindung auf dem Server. |
| data_sensitivity_information | nvarchar(4000) | **Gilt für**: nur Azure SQL-DB<br /><br /> Informationstypen und Vertraulichkeits Bezeichnungen, die von der überwachten Abfrage zurückgegeben werden, basierend auf den klassifizierten Spalten in der Datenbank. Weitere Informationen zum [ermitteln und Klassifizieren von Daten in Azure SQL-Datenbanken](https://docs.microsoft.com/azure/sql-database/sql-database-data-discovery-and-classification) |
| Datenbankname | **sysname** | Der Datenbankkontext, in dem die Aktion aufgetreten ist. Lässt NULL-Werte zu. Gibt NULL für Überwachungen auf Serverebene zurück. |  
| database_principal_id | **int** |ID des Datenbankbenutzerkontexts, in dem die Aktion ausgeführt wird. Lässt keine NULL-Werte zu. Wenn dies nicht anwendbar ist, wird 0 zurückgegeben. Zum Beispiel bei einem Servervorgang.|
| database_principal_name | **sysname** | Aktueller Benutzer. Lässt NULL-Werte zu. Gibt NULL zurück, wenn nicht verfügbar. |  
| duration_milliseconds | **bigint** | **Gilt für**: Azure SQL-Datenbank und verwaltete Instanz<br /><br /> Ausführungsdauer der Abfrage in Millisekunden |
| event_time | **datetime2** | Datum und Uhrzeit, zu der die überprüfbare Aktion ausgelöst wird. Lässt keine NULL-Werte zu. |  
| file_name | **varchar (260)** | Der Pfad und der Name der Überwachungsprotokolldatei, aus der der Datensatz stammt. Lässt keine NULL-Werte zu. |
| is_column_permission | **bit** | Flag, das angibt, ob dies eine Berechtigung auf Spaltenebene ist. Lässt keine NULL-Werte zu. Gibt 0 zurück wenn permission_bitmask = 0.<br /> 1 = TRUE<br /> 0 = false |
| object_id | **int** | Die ID der Entität, bei der die Überwachung aufgetreten ist. Dazu gehören:<br /> Server Objekte<br /> Datenbanken<br /> Datenbankobjekte<br /> Schemaobjekte<br /> Lässt keine NULL-Werte zu. Gibt 0 zurück, wenn die Entität der Server selbst ist oder die Überwachung nicht auf Objektebene durchgeführt wird. Zum Beispiel bei der Authentifizierung. |  
| object_name | **sysname** | Der Name der Entität, bei der die Überwachung aufgetreten ist. Dazu gehören:<br /> Server Objekte<br /> Datenbanken<br /> Datenbankobjekte<br /> Schemaobjekte<br /> Lässt NULL-Werte zu. Gibt NULL zurück, wenn die Entität der Server selbst ist oder die Überwachung nicht auf Objektebene durchgeführt wird. Zum Beispiel bei der Authentifizierung. |
| permission_bitmask | **varbinary(16)** | In einigen Aktionen sind dies die Berechtigungen, die gewährt, verweigert oder widerrufen wurden. |
| response_rows | **bigint** | **Gilt für**: Azure SQL-Datenbank und verwaltete Instanz<br /><br /> Anzahl der Zeilen, die im Resultset zurückgegeben werden. |  
| schema_name | **sysname** | Der Schemakontext, in dem die Aktion aufgetreten ist. Lässt NULL-Werte zu. Gibt NULL für Überwachungen zurück, die außerhalb eines Schemas auftreten. |  
| sequence_group_id | **varbinary** | **Gilt für**: nur SQL Server (beginnend mit 2016)<br /><br />  Eindeutiger Bezeichner |  
| sequence_number | **int** | Hält die Reihenfolge der Datensätze innerhalb eines einzelnen Überwachungsdatensatzes fest, der zu groß für den Schreibpuffer für Überwachungen ist. Lässt keine NULL-Werte zu. |  
| server_instance_name | **sysname** | Der Name der Serverinstanz, in der die Überwachung aufgetreten ist. Das Standardformat Server\Instanz wird verwendet. |  
| server_principal_id | **int** | ID des Anmeldekontexts, in dem die Aktion ausgeführt wird. Lässt keine NULL-Werte zu. |  
| server_principal_name | **sysname** | Aktuelle Anmeldung. Lässt NULL-Werte zu. |  
| server_principal_sid | **varbinary** | Aktuelle Anmeldungs-SID. Lässt NULL-Werte zu. |  
| session_id | **smallint** | Die ID der Sitzung, in der das Ereignis aufgetreten ist. Lässt keine NULL-Werte zu. |  
| session_server_principal_name | **sysname** | Der Server Prinzipal für die Sitzung. Lässt NULL-Werte zu. |  
| statement | **nvarchar(4000)** | TSQL-Anweisung, falls vorhanden. Lässt NULL-Werte zu. Falls nicht zutreffend, wird NULL zurückgegeben. |  
| succeeded | **bit** | Gibt an, ob die Aktion erfolgreich ausgelöst wurde. Lässt keine NULL-Werte zu. Für alle Ereignisse außer Anmeldeereignisse meldet dies nur, ob die Berechtigungsüberprüfung erfolgreich war oder fehlgeschlagen ist, nicht der Vorgang.<br /> 1 = Erfolg<br /> 0 = Fehler |
| target_database_principal_id | **int** | Der Datenbankprinzipal, auf dem der GRANT/DENY/REVOKE-Vorgang ausgeführt wird. Lässt keine NULL-Werte zu. Falls nicht zutreffend, wird 0 zurückgegeben. |  
| target_database_principal_name | **sysname** | Der Ziel Benutzer der Aktion. Lässt NULL-Werte zu. Falls nicht zutreffend, wird NULL zurückgegeben. |  
| target_server_principal_id | **int** | Serverprinzipal, auf dem der GRANT/DENY/REVOKE-Vorgang ausgeführt wird. Lässt keine NULL-Werte zu. Falls nicht zutreffend, wird 0 zurückgegeben. |  
| target_server_principal_name | **sysname** | Ziel Anmeldung der Aktion. Lässt NULL-Werte zu. Falls nicht zutreffend, wird NULL zurückgegeben. |  
| target_server_principal_sid | **varbinary** | SID der Ziel Anmeldung. Lässt NULL-Werte zu. Falls nicht zutreffend, wird NULL zurückgegeben. |  
| transaction_id | **bigint** | **Gilt für**: nur SQL Server (beginnend mit 2016)<br /><br /> Eindeutiger Bezeichner zur Identifizierung mehrerer Überwachungs Ereignisse in einer Transaktion |  
| user_defined_event_id | **smallint** | **Gilt für**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], Azure SQL-Datenbank und verwaltete Instanz<br /><br /> Die benutzerdefinierte Ereignis-ID wurde als Argument an **sp_audit_write**übermittelt. **Null** für Systemereignisse (Standard) und ungleich 0 (null) für ein benutzerdefiniertes Ereignis. Weitere Informationen finden Sie unter [sp_audit_write &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-audit-write-transact-sql.md). |  
| user_defined_information | **nvarchar(4000)** | **Gilt für**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], Azure SQL-Datenbank und verwaltete Instanz<br /><br /> Wird verwendet, um zusätzliche Informationen aufzuzeichnen, die der Benutzer mithilfe der gespeicherten Prozedur **sp_audit_write** im Überwachungs Protokoll aufzeichnen möchte. |  

  
## <a name="remarks"></a>Bemerkungen  
 Wenn das an **fn_get_audit_file** über gegebene *file_pattern* -Argument auf einen Pfad oder eine Datei verweist, die nicht vorhanden ist, oder wenn die Datei keine Überwachungs Datei ist, wird die **MSG_INVALID_AUDIT_FILE** -Fehlermeldung zurückgegeben.  
  
## <a name="permissions"></a>Berechtigungen

- **SQL Server**: erfordert die **Control Server** -Berechtigung.  
- **Azure SQL**-Datenbank: erfordert die **Control Database** -Berechtigung.     
  - Server Administratoren können auf Überwachungs Protokolle aller Datenbanken auf dem Server zugreifen.
  - Administratoren, die nicht Server sind, können nur auf Überwachungs Protokolle aus der aktuellen Datenbank zugreifen.
  - Blobdateien, die die oben genannten Kriterien nicht erfüllen, werden übersprungen (eine Liste der übersprungenen blobdateien wird in der Abfrageausgabe Meldung angezeigt), und die Funktion gibt Protokolle nur aus blobdateien zurück, für die der Zugriff zulässig ist.  
  
## <a name="examples"></a>Beispiele

- **SQL Server**

  Dieses Beispiel liest aus einer Datei namens `\\serverName\Audit\HIPAA_AUDIT.sqlaudit`.  
  
  ```  
  SELECT * FROM sys.fn_get_audit_file ('\\serverName\Audit\HIPAA_AUDIT.sqlaudit',default,default);  
  GO  
  ```  

- **Azure SQL-Datenbank**

  In diesem Beispiel wird aus einer Datei mit dem Namen `ShiraServer/MayaDB/SqlDbAuditing_Audit/2017-07-14/10_45_22_173_1.xel` gelesen:  
  
  ```  
  SELECT * FROM sys.fn_get_audit_file ('https://mystorage.blob.core.windows.net/sqldbauditlogs/ShiraServer/MayaDB/SqlDbAuditing_Audit/2017-07-14/10_45_22_173_1.xel',default,default);
  GO  
  ```  

  Dieses Beispiel liest aus derselben Datei wie oben, jedoch mit zusätzlichen T-SQL-Klauseln (**Top**, **Order by**und **Where** -Klausel zum Filtern der Überwachungsdaten Sätze, die von der-Funktion zurückgegeben werden):
  
  ```  
  SELECT TOP 10 * FROM sys.fn_get_audit_file ('https://mystorage.blob.core.windows.net/sqldbauditlogs/ShiraServer/MayaDB/SqlDbAuditing_Audit/2017-07-14/10_45_22_173_1.xel',default,default)
  WHERE server_principal_name = 'admin1'
  ORDER BY event_time
  GO
  ```  

  In diesem Beispiel werden alle Überwachungs Protokolle von Servern, die mit `Sh` beginnen, gelesen: 
  
  ```  
  SELECT * FROM sys.fn_get_audit_file ('https://mystorage.blob.core.windows.net/sqldbauditlogs/Sh',default,default);
  GO  
  ```

Ein vollständiges Beispiel für das Erstellen einer Überwachung finden Sie unter [SQL Server Audit &#40;Datenbank-Engine&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).

Informationen zum Einrichten der Azure SQL-Daten Bank Überwachung finden [Sie unter "Einstieg in die SQL-Daten Bank](https://docs.microsoft.com/azure/sql-database/sql-database-auditing)Überwachung".
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [CREATE SERVER AUDIT &#40;Transact-SQL&#41;](../../t-sql/statements/create-server-audit-transact-sql.md)   
 [ALTER SERVER AUDIT &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [DROP SERVER AUDIT &#40;Transact-SQL&#41;](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [CREATE SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [ALTER SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [DROP SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [CREATE DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [ALTER DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
 [DROP DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sys.server_audits &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [sys.server_file_audits &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [sys.server_audit_specifications &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [sys.server_audit_specification_details &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)   
 [sys.database_audit_specifications &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [sys.database_audit_specification_details &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [sys.dm_server_audit_status &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [sys.dm_audit_actions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [sys.dm_audit_class_type_map &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [Erstellen einer Serverüberwachung und einer Serverüberwachungsspezifikation](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
