---
title: CDC. fn_cdc_get_net_changes_&lt;Capture_instance&gt; (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- fn_cdc_get_net_changes_<capture_instance>
- change data capture [SQL Server], querying metadata
- cdc.fn_cdc_get_net_changes_<capture_instance>
ms.assetid: 43ab0d1b-ead4-471c-85f3-f6c4b9372aab
author: rothja
ms.author: jroth
ms.openlocfilehash: 77fb03c71bd0773cc8f004a89c28c1925284876b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68043046"
---
# <a name="cdcfncdcgetnetchangesltcaptureinstancegt-transact-sql"></a>CDC. fn_cdc_get_net_changes_&lt;Capture_instance&gt; (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt eine nettoänderungszeile für jede Quellzeile geändert im angegebenen Bereich (Log Sequence Zahlen, LSN) zurück.  
  
 **Warten Sie, was einer LSN ist?** Jeder Datensatz in die [SQL Server-Transaktionsprotokoll](../logs/the-transaction-log-sql-server.md) wird eindeutig durch eine protokollfolgenummer (LSN) identifiziert. LSNs sind sortiert, sodass Wenn LSN2 größer als LSN1 ist, der durch den Protokolldatensatz von LSN2 beschriebene Änderung **nach** die Änderung durch den Protokolldatensatz beschrieben wird.  
  
 Die LSN eines Protokolldatensatzes, wo ein wichtiges Ereignis aufgetreten ist, kann zum Erstellen richtiger wiederherstellungssequenzen hilfreich sein. Da lsns eine bestimmte Reihenfolge aufweisen, können Sie diese auf Gleichheit und Ungleichheit vergleichen (d. h. \<, >, =, \<=, > =). Solche Vergleiche sind beim Erstellen von Wiederherstellungssequenzen hilfreich.  
  
 Wenn eine Quellzeile mehrere Änderungen während des LSN-Bereichs ist, wird eine einzelne Zeile, die den endgültigen Inhalt der Zeile wiedergibt, von der enumerationsfunktion, die unten beschriebenen zurückgegeben. Z. B. wenn eine Transaktion eine Zeile in der Quelltabelle fügt aus, und eine nachfolgende Transaktion innerhalb des LSN-Bereichs eine oder mehrere Spalten in dieser Zeile aktualisiert, gibt die Funktion nur **eine** Zeile, die den aktualisierten Spaltenwerten.  
  
 Diese Enumerationsfunktion wird erstellt, wenn eine Quelltabelle für Change Data Capture aktiviert wird und die Nettonachverfolgung angegeben ist. Um die Nettonachverfolgung zu aktivieren, muss die Quelltabelle einen Primärschlüssel oder einen eindeutigen Index aufweisen. Der Funktionsname wird abgeleitet und verwendet das Format CDC. fn_cdc_get_net_changes_*Capture_instance*, wobei *Capture_instance* ist der Wert für die Aufzeichnungsinstanz angegeben wird, wenn die Quelltabelle wurde für Change Data Capture aktiviert. Weitere Informationen finden Sie unter [Sys. sp_cdc_enable_table &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md).  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
cdc.fn_cdc_get_net_changes_capture_instance ( from_lsn , to_lsn , '<row_filter_option>' )  
  
<row_filter_option> ::=  
{ all  
 | all with mask  
 | all with merge  
}  
```  
  
## <a name="arguments"></a>Argumente  
 *from_lsn*  
 Legen Sie die LSN, die den unteren Endpunkt des LSN-Bereichs, in das Resultset aufgenommen darstellt. *From_lsn* ist **("Binary(10)")** .  
  
 Nur Zeilen aus der [cdc.&#91; Capture_instance&#93;_CT](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md) Änderungstabelle mit einem Wert in __ $Start_lsn größer als oder gleich *From_lsn* in das Resultset enthalten sind.  
  
 *to_lsn*  
 Legen Sie die LSN, die den oberen Endpunkt des LSN-Bereichs, in das Resultset aufgenommen darstellt. *To_lsn* ist **("Binary(10)")** .  
  
 Nur Zeilen aus der [cdc.&#91; Capture_instance&#93;_CT](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md) Änderungstabelle mit einem Wert in __ $Start_lsn kleiner als oder gleich *From_lsn* gleich *To_lsn* in das Resultset enthalten sind.  
  
 *< Row_filter_option >* :: = {alle | alle mit der Maske | mit Merge}  
 Eine Option, die den Inhalt der Metadatenspalten sowie die im Resultset zurückgegebenen Zeilen bestimmt. Eine der folgenden Optionen ist möglich:  
  
 all  
 Gibt die LSN der letzten zeilenänderung sowie den Vorgang zum Anwenden der Zeile in den Metadatenspalten __ $Start_lsn und \_ \_$operation. Die Spalte \_ \_$Update_mask ist immer NULL.  
  
 all with mask  
 Gibt die LSN der letzten zeilenänderung sowie den Vorgang zum Anwenden der Zeile in den Metadatenspalten __ $Start_lsn und \_ \_$operation. Darüber hinaus, wenn ein Update-Vorgang zurückgegeben (\_\_$operation = 4) im Update geänderten aufgezeichneten Spalten werden in den zurückgegebenen Wert markiert \_ \_$Update_mask.  
  
 all with merge  
 Gibt die LSN der letzten Zeilenänderung in den Metadatenspalten __$start_lsn zurück. Die Spalte \_ \_$operation werden einen von zwei Werten: 1 für löschen oder 5 als Hinweis dafür, dass der Vorgang erforderlich, um die Änderung zu übernehmen, entweder ein Einfügevorgang oder ein Update ist. Die Spalte \_ \_$Update_mask ist immer NULL.  
  
 Da die Bestimmung des präzisen Vorgangs für eine bestimmte Änderung die Logik der Abfragekomplexität erhöht, soll diese Option die Abfrageleistung in den Fällen verbessern, in denen zur Angabe des für die Änderungsanwendung notwendigen Vorgangs nur darauf hingewiesen werden muss, dass es sich entweder um einen Einfügevorgang oder um einen Updatevorgang handelt, und die explizite Unterscheidung der beiden Vorgänge nicht notwendig ist. Diese Option eignet sich besonders für Zielumgebungen, in denen Mergevorgänge direkt verfügbar sind, z. B. in einer [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Umgebung.  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|__$start_lsn|**binary(10)**|LSN, die dem Commit für die Änderung zugeordnet wurde.<br /><br /> Alle Änderungen, für die ein Commit in derselben Transaktion ausgeführt wurde, verwenden dieselbe Commit-LSN. Z. B. bei einem Updatevorgang in der Quelltabelle zwei Spalten in zwei Zeilen geändert werden, enthält die Änderungstabelle vier Zeilen, die jeweils mit der gleichen __ $Start_lsnvalue.|  
|__$operation|**int**|Identifiziert den Vorgang der Datenbearbeitungssprache (Data Manipulation Language, DML), der erforderlich ist, um die Zeile der Änderungsdaten auf die Zieldatenquelle anzuwenden.<br /><br /> Wenn der Wert des row_filter_option-Parameters 'all' oder 'all with mask' ist, kann der Wert in dieser Spalte einen der folgenden Werte annehmen:<br /><br /> 1 = Löschen<br /><br /> 2 = Einfügen<br /><br /> 4 = Aktualisieren<br /><br /> Wenn der Wert des row_filter_option-Parameters 'all with merge' ist, kann der Wert in dieser Spalte einen der folgenden Werte annehmen:<br /><br /> 1 = Löschen|  
|__$update_mask|**varbinary(128)**|Eine Bitmaske mit einem Bit, das den einzelnen aufgezeichneten Spalten entspricht, die für die Aufzeichnungsinstanz identifiziert wurden. Für diesen Wert sind alle definierten Bits auf 1 festgelegt, wenn __$operation = 1 oder 2 ist. Wenn \_ \_$operation = 3 oder 4, nur die bits, die geänderten Spalten entsprechen, die auf 1 festgelegt werden.|  
|*\<erfasste Quelltabellenspalten>*|variiert|Bei den von der Funktion zurückgegebenen verbleibenden Spalten handelt es sich um die Spalten aus der Quelltabelle, die beim Erstellen der Aufzeichnungsinstanz als aufgezeichnete Spalten identifiziert wurden. Wenn in der Liste der aufgezeichneten Spalten keine Spalten angegeben wurden, werden alle Spalten in der Quelltabelle zurückgegeben.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle sysadmin oder in der festen Datenbankrolle db_owner. Für alle anderen Benutzer ist die SELECT-Berechtigung für alle aufgezeichneten Spalten in der Quelltabelle und, wenn eine Gatingrolle für die Aufzeichnungsinstanz definiert wurde, eine Mitgliedschaft in dieser Datenbankrolle erforderlich. Wenn der Aufrufer nicht über die Berechtigungen zum Anzeigen der Quelldaten verfügt, gibt die Funktion Fehler 208 (Ungültiger Objektname) zurück.  
  
## <a name="remarks"></a>Hinweise  
 Wenn der angegebene LSN-Bereich nicht in den Zeitraum der Änderungsnachverfolgung der Aufzeichnungsinstanz fällt, gibt die Funktion Fehler 208 (Ungültiger Objektname) zurück.

 Änderungen an der eindeutige Bezeichner einer Zeile führt dazu, dass Fn_cdc_get_net_changes zum Anzeigen von des ersten UPDATE-Befehls mit einer DELETE, und klicken Sie dann stattdessen INSERT-Befehl.  Dieses Verhalten ist erforderlich, den Schlüssel vor und nach der Änderung zu verfolgen.
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Funktion `cdc.fn_cdc_get_net_changes_HR_Department` zum Melden von Änderungen an der Quelltabelle vorgenommenen `HumanResources.Department` während eines bestimmten Zeitintervalls.  
  
 Zuerst wird die `GETDATE`-Funktion verwendet, um den Anfang des Zeitintervalls zu markieren. Nachdem mehrere DML-Anweisungen auf die Quelltabelle angewendet wurden, wird die `GETDATE`-Funktion erneut aufgerufen, um das Ende des Zeitintervalls zu identifizieren. Die Funktion [Sys. fn_cdc_map_time_to_lsn](../../relational-databases/system-functions/sys-fn-cdc-map-time-to-lsn-transact-sql.md) wird dann verwendet, um das Zeitintervall Change Data Capture Abfragebereichs begrenzt durch den LSN-Werten zuzuordnen. Schließlich wird die `cdc.fn_cdc_get_net_changes_HR_Department`-Funktion abgefragt, um die Nettoänderungen an der Quelltabelle für das Zeitintervall zu erhalten. Beachten Sie, dass die eingefügte und anschließend gelöschte Zeile nicht in dem von der Funktion zurückgegebenen Resultset aufgeführt wird. Der Grund dafür ist, dass eine in einem Abfragefenster zuerst hinzugefügte und dann gelöschte Zeile keine Nettoänderung in der Quelltabelle für das Intervall erzeugt. Bevor Sie dieses Beispiel ausführen, müssen Sie zunächst Beispiel B im ausführen [Sys. sp_cdc_enable_table &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md).  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @begin_time datetime, @end_time datetime, @from_lsn binary(10), @to_lsn binary(10);  
-- Obtain the beginning of the time interval.  
SET @begin_time = GETDATE() -1;  
-- DML statements to produce changes in the HumanResources.Department table.  
INSERT INTO HumanResources.Department (Name, GroupName)  
VALUES (N'MyDept', N'MyNewGroup');  
  
UPDATE HumanResources.Department  
SET GroupName = N'Resource Control'  
WHERE GroupName = N'Inventory Management';  
  
DELETE FROM HumanResources.Department  
WHERE Name = N'MyDept';  
  
-- Obtain the end of the time interval.  
SET @end_time = GETDATE();  
-- Map the time interval to a change data capture query range.  
SET @from_lsn = sys.fn_cdc_map_time_to_lsn('smallest greater than or equal', @begin_time);  
SET @to_lsn = sys.fn_cdc_map_time_to_lsn('largest less than or equal', @end_time);  
  
-- Return the net changes occurring within the query window.  
SELECT * FROM cdc.fn_cdc_get_net_changes_HR_Department(@from_lsn, @to_lsn, 'all');  
```  
  
## <a name="see-also"></a>Siehe auch  
 [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)   
 [sys.fn_cdc_map_time_to_lsn &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-cdc-map-time-to-lsn-transact-sql.md)   
 [sys.sp_cdc_enable_table &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md)   
 [sys.sp_cdc_help_change_data_capture &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)   
 [Über Change Data Capture &#40;SQL Server&#41;](../../relational-databases/track-changes/about-change-data-capture-sql-server.md)  
  
  
