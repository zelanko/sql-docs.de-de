---
title: Ändern von speicheroptimierten Tabellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 690b70b7-5be1-4014-af97-54e531997839
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4d1ae35d9dae03292edf31cd2b06acf97dc0db0c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "72783239"
---
# <a name="altering-memory-optimized-tables"></a>Ändern von speicheroptimierten Tabellen
  Das Ausführen von Änderungsvorgängen (ALTER) in speicheroptimierten Tabellen wird nicht unterstützt. Hierzu zählen beispielsweise das Ändern von bucket_count, das Hinzufügen oder Entfernen eines Indexes und das Hinzufügen oder Entfernen einer Spalte. Dieses Thema stellt Richtlinien zum Aktualisieren speicheroptimierter Tabellen bereit.  
  
## <a name="updating-the-definition-of-a-memory-optimized-table"></a>Aktualisieren der Definition einer speicheroptimierten Tabelle  
 Zum Aktualisieren der Definition einer speicheroptimierten Tabelle müssen Sie eine neue Tabelle mit der aktualisierten Tabellendefinition erstellen, die Daten in die neue Tabelle kopieren und festlegen, dass ab jetzt die neue Tabelle verwendet werden soll. Wenn die Tabelle nicht schreibgeschützt ist, muss hierfür die Arbeitsauslastung der Tabelle beendet werden, um sicherzustellen, dass keine Änderungen an der Tabelle vorgenommen werden, während die Daten kopiert werden.  
  
 Im folgenden Verfahren werden die notwendigen Schritte zum Aktualisieren einer Tabelle veranschaulicht. In diesem Beispiel wird durch das Update ein Index hinzugefügt. Dieses Verfahren behält den Namen der Tabelle bei und erfordert zwei Datenkopiervorgänge: einmal in eine temporäre Tabelle und einmal in die neue Tabelle. Das Ändern von bucket_count für einen Index oder das Hinzufügen und Entfernen einer Spalte können auf die gleiche Weise erfolgen.  
  
1.  Beenden Sie die Arbeitsauslastung für die Tabelle.  
  
2.  Generieren Sie ein Skript für die Tabelle, und fügen Sie dem Skript den neuen Index hinzu.  
  
3.  Generieren Sie ein Skript für die schemagebundenen Objekte (hauptsächlich systemintern kompilierte gespeicherte Prozeduren), die auf T verweisen, und für deren Berechtigungen.  
  
     Die schemagebundenen Objekte, die auf die Tabelle verweisen, können mit der folgenden Abfrage ermittelt werden:  
  
    ```sql  
    declare @t nvarchar(255) = N'<table name>'  
  
    select r.referencing_schema_name, r.referencing_entity_name  
    from sys.dm_sql_referencing_entities (@t, 'OBJECT') as r join sys.sql_modules m on r.referencing_id=m.object_id  
    where r.is_caller_dependent = 0 and m.is_schema_bound=1;  
    ```  
  
     Ein Skript für die Berechtigungen einer gespeicherten Prozedur kann mit folgendem [!INCLUDE[tsql](../../includes/tsql-md.md)]-Code geschrieben werden:  
  
    ```sql  
    declare @sp nvarchar(255) = N'<procedure name>'  
    declare @permissions nvarchar(max) = N''  
  
    select @permissions += dp.state_desc + N' ' + dp.permission_name + N' ON ' +   
       quotename(schema_name(o.schema_id)) + N'.' + quotename(o.name) + N' TO ' +  
       quotename(u.name) + N'; ' + char(13)  
    from sys.database_permissions as dp  
  
    join sys.database_principals as u  
       on u.principal_id = dp.grantee_principal_id  
  
    join sys.objects as o  
       on o.object_id = dp.major_id  
    where dp.class = 1 /* object */  
       and dp.minor_id = 0 and o.object_id=object_id(@sp);  
  
    select @permissions  
    ```  
  
4.  Erstellen Sie eine Kopie der Tabelle, und kopieren Sie die Daten aus der ursprünglichen Tabelle in die Tabellenkopie. Die Kopie kann mit den folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)] <sup>1</sup>erstellt werden.  
  
    ```sql  
    select * into dbo.T_copy from dbo.T  
    ```  
  
     Wenn genügend Arbeitsspeicher verfügbar ist, `T_copy` kann eine Speicher optimierte Tabelle sein, wodurch die Daten schneller kopiert werden. <sup>2</sup>  
  
5.  Löschen Sie die schemagebundenen Objekte, die auf die ursprüngliche Tabelle verweisen.  
  
6.  Löschen Sie die ursprüngliche Tabelle.  
  
7.  Erstellen Sie die neue Tabelle (`T`) mit dem Skript, das den neuen Index enthält.  
  
8.  Kopieren Sie die Daten von `T_copy` nach `T`.  
  
9. Erstellen Sie die verweisenden schemagebundenen Objekte neu, und wenden Sie die Berechtigungen an.  
  
10. Starten Sie die Arbeitsauslastung auf `T`.  
  
 <sup>1</sup> beachten Sie `T_copy` , dass in diesem Beispiel auf dem Datenträger persistent gespeichert wird. Wenn eine Sicherung von `T` verfügbar ist, kann `T_copy` eine nicht dauerhafte oder eine temporäre Tabelle sein.  
  
 <sup>2</sup> es muss genügend Arbeitsspeicher für `T_copy`vorhanden sein. Der Arbeitsspeicher wird bei `DROP TABLE` nicht sofort freigegeben. Wenn `T_copy` speicheroptimiert ist, muss genügend Arbeitsspeicher für zwei zusätzliche Kopien von `T` verfügbar sein. Wenn `T_copy` eine datenträgerbasierte Tabelle ist, wird nur Speicher für eine zusätzliche Kopie von `T` benötigt, da der Garbage Collector erst entsprechende Schritte ausführen muss, nachdem die alte Version von `T` gelöscht wurde.  
  
## <a name="changing-schema-powershell"></a>Ändern des Schemas (PowerShell)  
 Die folgenden PowerShell-Skripts bereiten Schemaänderungen vor und generieren diese, indem Skripts für die Tabelle und die zugehörigen Berechtigungen erstellt werden.  
  
```powershell
prepare_schema_change.ps1 <serverName> <databaseName> <schemaName> <tableName>
```
  
 Dieses Skript erwartet als Argumente eine Tabelle und erstellt im aktuellen Ordner ein Skript für das Objekt und dessen Berechtigungen sowie für verweisende schemagebundene Objekte und deren Berechtigungen. Insgesamt werden 7 Skripts für das Aktualisieren des Schemas der Eingabetabelle generiert:  
  
-   Kopiert Daten in eine temporäre Tabelle (einen Heap).  
  
-   Löscht schemagebundene Objekte, die auf die Tabelle verweisen.  
  
-   Löschen Sie die Tabelle.  
  
-   Erstellt die Tabelle mit dem neuen Schema neu und wendet die Berechtigungen erneut an.  
  
-   Kopiert die Daten aus der temporären Tabelle in die neu erstellte Tabelle.  
  
-   Erstellt die schemagebundenen Objekte, die auf die Tabelle verweisen, und deren Berechtigungen neu.  
  
-   Löscht die temporäre Tabelle.  
  
 Das Skript für Schritt 4 sollte entsprechend geändert werden, um die gewünschten Schemaänderungen festzulegen. Wenn in den Spalten der Tabelle Änderungen vorgenommen werden, sollten die Skripts für die Schritte 5 (Kopieren von Daten aus temporärer Tabelle) und 6 (gespeicherte Prozeduren neu erstellen) nach Bedarf aktualisiert werden.  
  
```powershell
# Prepare for schema changes by scripting out the table, as well as associated permissions
# Usage: prepare_schema_change.ps1 server_name db_name schema_name table_name  
# stop execution once an error occurs  
$ErrorActionPreference="Stop"  
  
if($args.Count -le 3)  
{  
   throw "Usage prepare_schema_change.ps1 server_name db_name schema_name table_name"  
}  
  
$servername = $args[0]  
$database = $args[1]  
$schema = $args[2]  
$object = $args[3]  
  
$object_heap = "$object$(Get-Random)"  
  
[System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.SMO") | Out-Null  
  
$server =  New-Object ("Microsoft.SqlServer.Management.SMO.Server") ($servername)  
$scripter = New-Object ("Microsoft.SqlServer.Management.SMO.Scripter") ($server)  
  
## initialize table variable  
$tableUrn = $server.Databases[$database].Tables[$object, $schema]  
if($tableUrn.Count -eq 0)  
{  
   throw "Table or database not found"  
}  
  
## initialize scripting object  
$scriptingOptions = New-Object ("Microsoft.SqlServer.Management.SMO.ScriptingOptions")
$scriptingOptions.Permissions = $True  
$scriptingOptions.ScriptDrops = $True  
  
$scripter.Options = $scriptingOptions;  
  
Write-Host "(1) Scripting SELECT INTO $object_heap for table [$object] to 1_copy_to_heap_for_$schema`_$object.sql"  
Echo "SELECT * INTO $schema.$object_heap FROM $schema.$object WITH (SNAPSHOT)" | Out-File "1_copy_to_heap_$schema`_$object.sql";  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(2) Scripting DROP for procs schema-bound to [$object] 2_drop_procs_$schema`_$object.sql"  
## query referencing schema-bound objects  
$dt = $server.Databases[$database].ExecuteWithResults("select r.referencing_schema_name, r.referencing_entity_name  
from sys.dm_sql_referencing_entities ('$schema.$object', 'OBJECT') as r join sys.sql_modules m on r.referencing_id=m.object_id  
where r.is_caller_dependent = 0 and m.is_schema_bound=1;")  
  
## initialize out file  
Echo "" | Out-File "2_drop_procs_$schema`_$object.sql"  
## loop through schema-bound objects  
ForEach ($t In $dt.Tables)  
{    
   ForEach ($r In $t.Rows)  
   {    
      ## script object   
      $so =  $server.Databases[$database].StoredProcedures[$r[1], $r[0]]  
      $scripter.Script($so) | Out-File -Append "2_drop_procs_$schema`_$object.sql"  
   }  
}  
Write-Host "--done--"  
Write-Host ""  
Write-Host "(3) Scripting DROP table for [$object] to 3_drop_table_$schema`_$object.sql"
$scripter.Script($tableUrn) | Out-File "3_drop_table_$schema`_$object.sql";
Write-Host "--done--"  
Write-Host ""  
  
## now script creates  
$scriptingOptions.ScriptDrops = $False  
  
Write-Host "(4) Scripting CREATE table and permissions for [$object] to !please_edit_4_create_table_$schema`_$object.sql"  
Write-Host "***** rename this script to 4_create_table.sql after completing the updates to the schema"
$scripter.Script($tableUrn) | Out-File "!please_edit_4_create_table_$schema`_$object.sql";  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(5) Scripting INSERT INTO table from heap and UPDATE STATISTICS for [$object] to 5_copy_from_heap_$schema`_$object.sql"  
Write-Host "[update this script if columns are added to or removed from the table]"  
Echo "INSERT INTO [$schema].[$object] SELECT * FROM [$schema].[$object_heap]; UPDATE STATISTICS [$schema].[$object] WITH FULLSCAN, NORECOMPUTE" | Out-File "5_copy_from_heap_$schema`_$object.sql";  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(6) Scripting CREATE PROC and permissions for procedures schema-bound to [$object] to 6_create_procs_$schema`_$object.sql"  
Write-Host "[update the procedure definitions if columns are renamed or removed]"  
## initialize out file  
Echo "" | Out-File "6_create_procs_$schema`_$object.sql"  
## loop through schema-bound objects  
ForEach ($t In $dt.Tables)  
{    
   ForEach ($r In $t.Rows)  
   {    
      ## script the schema-bound object  
      $so =  $server.Databases[$database].StoredProcedures[$r[1], $r[0]]  
      ForEach($s In $scripter.Script($so))  
        {  
            Echo $s | Out-File -Append "6_create_procs_$schema`_$object.sql"  
            Echo "GO" | Out-File -Append "6_create_procs_$schema`_$object.sql"  
        }  
   }  
}  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(7) Scripting DROP $object_heap to 7_drop_heap_$schema`_$object.sql"  
Echo "DROP TABLE $schema.$object_heap" | Out-File "7_drop_heap_$schema`_$object.sql";  
Write-Host "--done--"  
Write-Host ""  
```  
  
 Das folgende PowerShell-Skript führt die Schemaänderungen aus, für die im vorherigen Beispiel ein Skript erstellt wurde. Dieses Skript erwartet eine Tabelle als Argument und führt die Schemaänderungsskripts aus, die für diese Tabelle und die zugehörigen gespeicherten Prozeduren generiert wurden.  
  
 Verwendung: execute_schema_change. ps1 *server_name * * db_name`schema_name`table_name*  
  
```powershell
# stop execution once an error occurs  
$ErrorActionPreference="Stop"  
  
if($args.Count -le 3)  
{  
   throw "Usage execute_schema_change.ps1 server_name db_name schema_name table_name"  
}  
  
$servername = $args[0]  
$database = $args[1]  
$schema = $args[2]  
$object = $args[3]  
  
[System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.SMO") | Out-Null  
  
$server =  New-Object ("Microsoft.SqlServer.Management.SMO.Server") ($servername)  
$database = $server.Databases[$database]  
$table = $database.Tables[$object, $schema]  
if($table.Count -eq 0)  
{  
   throw "Table or database not found"  
}  
  
$1 = Get-Item "1_copy_to_heap_$schema`_$object.sql"  
$2 = Get-Item "2_drop_procs_$schema`_$object.sql"  
$3 = Get-Item "3_drop_table_$schema`_$object.sql"  
$4 = Get-Item "4_create_table_$schema`_$object.sql"  
$5 = Get-Item "5_copy_from_heap_$schema`_$object.sql"  
$6 = Get-Item "6_create_procs_$schema`_$object.sql"  
$7 = Get-Item "7_drop_heap_$schema`_$object.sql"  
  
Write-Host "(1) Running SELECT INTO heap for table [$object] from 1_copy_to_heap_for_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $1.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(2) Running DROP for procs schema-bound from [$object] 2_drop_procs_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $2.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(3) Running DROP table for [$object] to 4_drop_table_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $3.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(4) Running CREATE table and permissions for [$object] from 4_create_table_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $4.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(5) Running INSERT INTO table from heap for [$object] and UPDATE STATISTICS from 5_copy_from_heap_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $5.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(6) Running CREATE PROC and permissions for procedures schema-bound to [$object] from 6_create_procs_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $6.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(7) Running DROP heap from 7_drop_heap_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $7.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Speicher optimierte Tabellen](memory-optimized-tables.md)  
