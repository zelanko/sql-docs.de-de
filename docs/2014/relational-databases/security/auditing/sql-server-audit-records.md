---
title: SQL Server Audit-Datensätze | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- audit records [SQL Server]
ms.assetid: 7a291015-df15-44fe-8d53-c6d90a157118
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 3cc249ebfce796d7932e68d993ac98ede867845f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63238386"
---
# <a name="sql-server-audit-records"></a>SQL Server Audit-Datensätze
  Die Funktion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit ermöglicht es, Ereignisgruppen und Ereignisse auf Serverebene und auf Datenbankebene zu überwachen. Weitere Informationen finden Sie unter [SQL Server Audit &#40;Datenbank-Engine&#41;](sql-server-audit-database-engine.md). [https://login.microsoftonline.com/consumers/]([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]).  
  
 Überwachungen bestehen aus null oder mehr Überwachungsaktionselementen, die in einem *Überwachungsziel*aufgezeichnet werden. Beim Überwachungsziel kann es sich um eine Binärdatei, das Windows-Sicherheitsereignisprotokoll oder das Windows-Anwendungsereignisprotokoll handeln. Die an das Ziel gesendeten Datensätze können die in der folgenden Tabelle beschriebenen Elemente enthalten.  
  
|Spaltenname|BESCHREIBUNG|type|Immer verfügbar|  
|-----------------|-----------------|----------|----------------------|  
|**event_time**|Datum und Uhrzeit der Auslösung des überwachbaren Vorgangs.|`datetime2`|Ja|  
|**sequence_no**|Hält die Reihenfolge der Datensätze innerhalb eines einzelnen Überwachungsdatensatzes fest, der zu groß für den Schreibpuffer für Überwachungen ist.|`int`|Ja|  
|**action_id**|ID der Aktion<br /><br /> Tipp: Damit **action_id** als Prädikat verwendet werden kann, muss eine Konvertierung von einer Zeichenfolge in einen numerischen Wert durchgeführt werden. Weitere Informationen finden Sie unter [Filtern von SQL Server Audit nach dem action_id-Prädikat oder class_type-Prädikat](https://blogs.msdn.com/b/sqlsecurity/archive/2012/10/03/filter-sql-server-audit-on-action-id-class-type-predicate.aspx).|`varchar(4)`|Ja|  
|**succeeded**|Gibt an, ob die Aktion, die das Ereignis ausgelöst hat, erfolgreich war.|`bit`-1 = Erfolg, 0 = Fehler|Ja|  
|**permission_bitmask**|Zeigt die gewährten, verweigerten oder widerrufenen Berechtigungen an (falls verfügbar)|`bigint`|Nein|  
|**is_column_permission**|Flag, das eine Berechtigung auf Spaltenebene angibt.|`bit`-1 = true, 0 = false|Nein|  
|**session_id**|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|`int`|Ja|  
|**server_principal_id**|ID des Anmeldekontexts, in dem die Aktion ausgeführt wird.|`int`|Ja|  
|**database_principal_id**|ID des Datenbankbenutzerkontexts, in dem die Aktion ausgeführt wird.|`int`|Nein|  
|**object_ id**|Die primäre ID der Entität, bei der die Überwachung aufgetreten ist. Dies umfasst:<br /><br /> Serverobjekte<br /><br /> databases<br /><br /> Datenbankobjekte<br /><br /> Schemaobjekte|`int`|Nein|  
|**target_server_principal_id**|Serverprinzipal, für den die überwachbare Aktion gilt.|`int`|Ja|  
|**target_database_principal_id**|Datenbankprinzipal, für den die überwachbare Aktion gilt.|`int`|Nein|  
|**class_type**|Typ der überwachbaren Entität, bei der die Überwachung auftritt.|`varchar(2)`|Ja|  
|**session_server_principal_name**|Serverprinzipal für die Sitzung.|`sysname`|Ja|  
|**server_principal_name**|Aktuelle Anmeldung.|`sysname`|Ja|  
|**server_principal_sid**|Aktuelle Anmeldungs-SID.|`varbinary`|Ja|  
|**database_principal_name**|Aktueller Benutzer.|`sysname`|Nein|  
|**target_server_principal_name**|Zielanmeldung der Aktion.|`sysname`|Nein|  
|**target_server_principal_sid**|SID der Zielanmeldung.|`varbinary`|Nein|  
|**target_database_principal_name**|Zielbenutzer der Aktion.|`sysname`|Nein|  
|**server_instance_name**|Der Name der Serverinstanz, in der die Überwachung aufgetreten ist. Verwendet das standardmäßige machine\instance-Format.|`nvarchar(120)`|Ja|  
|**database_name**|Der Datenbankkontext, in dem die Aktion aufgetreten ist.|`sysname`|Nein|  
|**schema_name**|Schemakontext, in dem die Aktion durchgeführt wurde|`sysname`|Nein|  
|**object_name**|Name der Entität, für die die Überwachung durchgeführt wurde Dies umfasst:<br /><br /> Serverobjekte<br /><br /> databases<br /><br /> Datenbankobjekte<br /><br /> Schemaobjekte<br /><br /> TSQL-Anweisung (falls vorhanden)|`sysname`|Nein|  
|**an**|TSQL-Anweisung (falls vorhanden)|`nvarchar(4000)`|Nein|  
|**additional_information**|Zusätzliche Informationen über das als XML gespeicherte Ereignis.|`nvarchar(4000)`|Nein|  
  
## <a name="remarks"></a>Bemerkungen  
 Einige Aktionen geben nicht den Wert einer Spalte ein, da er auf die Aktion nicht anwendbar sein könnte.  
  
 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit speichert 4000 Datenzeichen für Zeichenfelder in einem Überwachungsdatensatz. Wenn die Werte **additional_information** und **statement** , die von einer überwachbaren Aktion zurückgegeben wurden, mehr als 4000 Zeichen zurückgeben, wird die Spalte **sequence_no** dazu verwendet, mehrere Datensätze in einen Überwachungsbericht für eine einzelne Überwachungsaktion zu schreiben, um diese Daten aufzuzeichnen. Dieser Prozess verläuft wie folgt:  
  
-   Die Spalte **statement** wird in 4000 Zeichen geteilt.  
  
-   
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit schreibt als erste Zeile für den Überwachungsdatensatz die partiellen Daten. Alle anderen Felder werden in jeder Zeile dupliziert.  
  
-   Der **sequence_no** -Wert wird inkrementiert.  
  
-   Dieser Prozess wird wiederholt, bis alle Daten aufgezeichnet wurden.  
  
 Sie können die Daten verbinden, indem Sie die Zeilen sequenziell mit dem Wert **sequence_no** und den Spalten **event_Time**, **action_id** sowie **session_id** lesen, um die Aktion zu identifizieren.  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [CREATE SERVER AUDIT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-audit-transact-sql)  
  
 [ALTER SERVER AUDIT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-audit-specification-transact-sql)  
  
 [DROP SERVER AUDIT &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-server-audit-transact-sql)  
  
 [CREATE SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-audit-specification-transact-sql)  
  
 [ALTER SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-audit-transact-sql)  
  
 [DROP SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-server-audit-specification-transact-sql)  
  
 [CREATE DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-database-audit-specification-transact-sql)  
  
 [ALTER DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-audit-specification-transact-sql)  
  
 [DROP DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-database-encryption-key-transact-sql)  
  
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-authorization-transact-sql)  
  
 [sys.fn_get_audit_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-get-audit-file-transact-sql)  
  
 [sys.server_audits &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-audits-transact-sql)  
  
 [sys.server_file_audits &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-file-audits-transact-sql)  
  
 [sys.server_audit_specifications &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql)  
  
 [sys.server_audit_specification_details &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql)  
  
 [sys.database_audit_specifications &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql)  
  
 [sys.database_audit_specification_details &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql)  
  
 [sys.dm_server_audit_status &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql)  
  
 [sys.dm_audit_actions &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql)  
  
 [sys.dm_audit_class_type_map &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql)  
  
  
