---
description: core.sp_purge_data (Transact-SQL)
title: Core. sp_purge_data (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_purge_data_TSQL
- sp_purge_data
dev_langs:
- TSQL
helpviewer_keywords:
- sp_purge_data
- management data warehouse, data collector stored procedures
- core.sp_purge_data stored procedure
- data collector [SQL Server], stored procedures
ms.assetid: 056076c3-8adf-4f51-8a1b-ca39696ac390
author: markingmyname
ms.author: maghan
ms.openlocfilehash: ff33927812ccab2f2665e80709bcf6074ebacc1a
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89530307"
---
# <a name="coresp_purge_data-transact-sql"></a>core.sp_purge_data (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Entfernt Daten basierend auf einer Beibehaltungsrichtlinie aus dem Verwaltungs-Data Warehouse. Diese Prozedur wird täglich vom mdw_purge_data-Auftrag des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agents für das Verwaltungs-Data Warehouse ausgeführt, das der angegebenen Instanz zugeordnet ist. Sie können mit dieser gespeicherten Prozedur Daten aus dem Verwaltungs-Data Warehouse bedarfsgesteuert entfernen.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
core.sp_purge_data  
    [ [ @retention_days = ] retention_days ]  
    [ , [ @instance_name = ] 'instance_name' ]  
    [ , [ @collection_set_uid = ] 'collection_set_uid' ]  
    [ , [ @duration = ] duration ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @retention_days =] *retention_days*  
 Die Anzahl der Tage für die Beibehaltung von Daten in den Verwaltungs-Data Warehouse-Tabellen. Daten mit einem Zeitstempel, der älter als *retention_days* ist, werden entfernt. *retention_days* ist vom Datentyp **smallint**. der Standardwert ist NULL. Wenn angegeben, muss der Wert positiv sein. Wenn der Wert NULL ist, legt der Wert in der valid_through-Spalte in der core.snapshots-Sicht die Zeilen fest, die entfernt werden können.  
  
 [ @instance_name =] '*instance_name*'  
 Der Name der Instanz für den Sammlungssatz. *instance_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
 *instance_name* muss der voll qualifizierte Instanzname sein, der aus dem Computernamen und dem Instanznamen im Format *Computername* \\ *instanceName*besteht. Wenn der Wert NULL ist, wird die Standardinstanz auf dem lokalen Server verwendet.  
  
 [ @collection_set_uid =] '*collection_set_uid*'  
 Die GUID für den Sammlungssatz. *collection_set_uid* ist vom Datentyp **uniqueidentifier**und hat den Standardwert NULL. Wenn der Wert NULL ist, werden die qualifizierenden Zeilen aus allen Sammlungssätzen entfernt. Um diesen Wert abzurufen, fragen Sie die syscollector_collection_sets-Katalogsicht ab.  
  
 [ @duration =] *Dauer*  
 Die maximale Anzahl der Minuten für die Ausführung des Entfernen-Vorgangs. *Duration* ist vom Datentyp **smallint**. der Standardwert ist NULL. Wenn dieser Wert angegeben ist, muss er 0 (null) oder eine positive ganze Zahl sein. Wenn der Wert NULL ist, wird der Vorgang so lange ausgeführt, bis alle gekennzeichneten Zeilen entfernt sind oder bis der Vorgang manuell beendet wird.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Diese Prozedur wählt Zeilen in der core.snapshots-Sicht aus, die in Abhängigkeit einer Beibehaltungsdauer entfernt werden können. Alle für die Entfernung gekennzeichneten Zeilen werden aus der core.snapshots_internal-Tabelle gelöscht. Das Löschen der vorangehenden Zeilen löst eine Löschweitergabe (cascading delete) in allen Verwaltungs-Data Warehouse-Tabellen aus. Dies wird durch die Verwendung der ON DELETE CASCADE-Klausel erzielt, die für alle Tabellen definiert wird, in denen gesammelte Daten gespeichert werden.  
  
 Jede Momentaufnahme wird mit den zugeordneten Daten in einer expliziten Transaktion gelöscht. Anschließend wird ein Commit ausgeführt. Wenn der Löschvorgang also manuell beendet oder der für angegebene Wert @duration überschritten wird, verbleiben nur die Daten, für die kein Commit ausgeführt wurde. Diese Daten können bei der nächsten Ausführung des Auftrags entfernt werden.  
  
 Die Prozedur muss im Kontext der Verwaltungs-Data Warehouse-Datenbank ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der Daten Bank Rolle " **mdw_admin** (mit EXECUTE-Berechtigung)".  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-running-sp_purge_data-with-no-parameters"></a>A. Ausführen von "sp_purge_data" ohne Parameter  
 Im folgenden Beispiel wird core.sp_purge_data ohne Angabe von Parametern ausgeführt. Daher wird der Standardwert NULL mit dem zugeordneten Verhalten für alle Parameter verwendet.  
  
```  
USE <management_data_warehouse>;  
EXECUTE core.sp_purge_data;  
GO  
```  
  
### <a name="b-specifying-retention-and-duration-values"></a>B. Angeben von Werten für Beibehalten und Dauer  
 Im folgenden Beispiel werden Daten aus dem Verwaltungs-Data Warehouse entfernt, die älter als 7 Tage sind. Außerdem wird der- @duration Parameter angegeben, sodass der Vorgang nicht länger als 5 Minuten ausgeführt wird.  
  
```  
USE <management_data_warehouse>;  
EXECUTE core.sp_purge_data @retention_days = 7, @duration = 5;  
GO  
```  
  
### <a name="c-specifying-an-instance-name-and-collection-set"></a>C. Angeben eines Instanznamens und eines Sammlungssatzes  
 Im folgenden Beispiel werden Daten aus dem Verwaltungs-Data Warehouse für einen bestimmten Sammlungssatz in der angegebenen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] entfernt. Da @retention_days nicht angegeben ist, wird der Wert in der valid_through-Spalte in der Core. Momentaufnahmen-Sicht verwendet, um die Zeilen für den Sammlungs Satz zu bestimmen, die entfernt werden können.  
  
```  
USE <management_data_warehouse>;  
GO  
-- Get the collection set unique identifier for the Disk Usage system collection set.  
DECLARE @disk_usage_collection_set_uid uniqueidentifier = (SELECT collection_set_uid   
    FROM msdb.dbo.syscollector_collection_sets WHERE name = N'Disk Usage');   
  
EXECUTE core.sp_purge_data @instance_name = @@SERVERNAME, @collection_set_uid = @disk_usage_collection_set_uid;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Gespeicherte Prozeduren für den Datensammler &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)  
  
  
