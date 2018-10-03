---
title: sp_purge_data (Transact-SQL) | Microsoft-Dokumentation
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cbcd8616fc743ee749b3adb9b30f343939fa7f3d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47819238"
---
# <a name="coresppurgedata-transact-sql"></a>core.sp_purge_data (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Entfernt Daten basierend auf einer Beibehaltungsrichtlinie aus dem Verwaltungs-Data Warehouse. Diese Prozedur wird täglich vom Mdw_purge_data ausgeführt[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Auftrag für das Management Datawarehouse, die mit der angegebenen Instanz verknüpft ist. Sie können mit dieser gespeicherten Prozedur Daten aus dem Verwaltungs-Data Warehouse bedarfsgesteuert entfernen.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
core.sp_purge_data  
    [ [ @retention_days = ] retention_days ]  
    [ , [ @instance_name = ] 'instance_name' ]  
    [ , [ @collection_set_uid = ] 'collection_set_uid' ]  
    [ , [ @duration = ] duration ]  
```  
  
## <a name="arguments"></a>Argumente  
 [@retention_days =] *Retention_days*  
 Die Anzahl der Tage für die Beibehaltung von Daten in den Verwaltungs-Data Warehouse-Tabellen. Daten mit einem Zeitstempel, die älter sind als *Retention_days* wird entfernt. *Retention_days* ist **Smallint**, hat den Standardwert NULL. Wenn angegeben, muss der Wert positiv sein. Wenn der Wert NULL ist, legt der Wert in der valid_through-Spalte in der core.snapshots-Sicht die Zeilen fest, die entfernt werden können.  
  
 [@instance_name =] '*Instance_name*"  
 Der Name der Instanz für den Sammlungssatz. *Instanzname* ist **Sysname**, hat den Standardwert NULL.  
  
 *Instanzname* muss der vollqualifizierte Instanzname sein, besteht aus den Namen des Computers und den Instanznamen im Format *Computername*\\*Instancename*. Wenn der Wert NULL ist, wird die Standardinstanz auf dem lokalen Server verwendet.  
  
 [@collection_set_uid =] '*Collection_set_uid*"  
 Die GUID für den Sammlungssatz. *Collection_set_uid* ist **Uniqueidentifier**, hat den Standardwert NULL. Wenn der Wert NULL ist, werden die qualifizierenden Zeilen aus allen Sammlungssätzen entfernt. Um diesen Wert abzurufen, fragen Sie die syscollector_collection_sets-Katalogsicht ab.  
  
 [@duration =] *Dauer*  
 Die maximale Anzahl der Minuten für die Ausführung des Entfernen-Vorgangs. *Dauer* ist **Smallint**, hat den Standardwert NULL. Wenn dieser Wert angegeben ist, muss er 0 (null) oder eine positive ganze Zahl sein. Wenn der Wert NULL ist, wird der Vorgang so lange ausgeführt, bis alle gekennzeichneten Zeilen entfernt sind oder bis der Vorgang manuell beendet wird.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Diese Prozedur wählt Zeilen in der core.snapshots-Sicht aus, die in Abhängigkeit einer Beibehaltungsdauer entfernt werden können. Alle für die Entfernung gekennzeichneten Zeilen werden aus der core.snapshots_internal-Tabelle gelöscht. Das Löschen der vorangehenden Zeilen löst eine Löschweitergabe (cascading delete) in allen Verwaltungs-Data Warehouse-Tabellen aus. Dies wird durch die Verwendung der ON DELETE CASCADE-Klausel erzielt, die für alle Tabellen definiert wird, in denen gesammelte Daten gespeichert werden.  
  
 Jede Momentaufnahme wird mit den zugeordneten Daten in einer expliziten Transaktion gelöscht. Anschließend wird ein Commit ausgeführt. Aus diesem Grund werden, wenn der entfernen-Vorgang manuell beendet oder der angegebene Wert für @duration überschritten wird, nur die nicht gespeicherte Daten bleiben. Diese Daten können bei der nächsten Ausführung des Auftrags entfernt werden.  
  
 Die Prozedur muss im Kontext der Verwaltungs-Data Warehouse-Datenbank ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **Mdw_admin** (mit EXECUTE-Berechtigung) festen Datenbankrolle.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-running-sppurgedata-with-no-parameters"></a>A. Ausführen von "sp_purge_data" ohne Parameter  
 Im folgenden Beispiel wird core.sp_purge_data ohne Angabe von Parametern ausgeführt. Daher wird der Standardwert NULL mit dem zugeordneten Verhalten für alle Parameter verwendet.  
  
```  
USE <management_data_warehouse>;  
EXECUTE core.sp_purge_data;  
GO  
```  
  
### <a name="b-specifying-retention-and-duration-values"></a>B. Angeben von Werten für Beibehalten und Dauer  
 Im folgenden Beispiel werden Daten aus dem Verwaltungs-Data Warehouse entfernt, die älter als 7 Tage sind. Darüber hinaus die @duration Parameter wird angegeben, sodass der Vorgang nicht länger als 5 Minuten ausgeführt wird.  
  
```  
USE <management_data_warehouse>;  
EXECUTE core.sp_purge_data @retention_days = 7, @duration = 5;  
GO  
```  
  
### <a name="c-specifying-an-instance-name-and-collection-set"></a>C. Angeben eines Instanznamens und eines Sammlungssatzes  
 Im folgenden Beispiel werden Daten aus dem Verwaltungs-Data Warehouse für einen bestimmten Sammlungssatz in der angegebenen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] entfernt. Da @retention_days nicht angegeben ist, wird der Wert in der Valid_through-Spalte in der core.snapshots-Sicht wird verwendet, um die Zeilen für den Sammlungssatz festzulegen, die entfernt werden.  
  
```  
USE <management_data_warehouse>;  
GO  
-- Get the collection set unique identifier for the Disk Usage system collection set.  
DECLARE @disk_usage_collection_set_uid uniqueidentifier = (SELECT collection_set_uid   
    FROM msdb.dbo.syscollector_collection_sets WHERE name = N'Disk Usage');   
  
EXECUTE core.sp_purge_data @instance_name = @@SERVERNAME, @collection_set_uid = @disk_usage_collection_set_uid;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Gespeicherte Prozeduren für den Datensammler &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)  
  
  
