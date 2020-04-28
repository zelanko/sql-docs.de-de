---
title: sp_showrowreplicainfo (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_showrowreplicainfo_TSQL
- sp_showrowreplicainfo
helpviewer_keywords:
- sp_showrowreplicainfo
ms.assetid: 6a9dbc1a-e1e1-40c4-97cb-8164a2288f76
author: stevestein
ms.author: sstein
ms.openlocfilehash: d0c750fd35dce98c1d754f192214cd96cfc56143
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68032893"
---
# <a name="sp_showrowreplicainfo-transact-sql"></a>sp_showrowreplicainfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Zeigt Informationen zu einer Zeile in einer Tabelle an, die als ein Artikel in einer Mergereplikation verwendet wird. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_showrowreplicainfo [ [ @ownername = ] 'ownername' ]  
    [ , [ @tablename =] 'tablename' ]   
        , [ @rowguid =] rowguid   
    [ , [ @show = ] 'show' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @ownername = ] 'ownername'`Der Name des Tabellen Besitzers. "Besitzer *Name* " ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Dieser Parameter ist hilfreich für differenzierte Tabellen, wenn eine Datenbank mehrere Tabellen mit dem gleichen Namen enthält, aber jede Tabelle einen unterschiedlichen Besitzer aufweist.  
  
`[ @tablename = ] 'tablename'`Der Name der Tabelle, die die Zeile enthält, für die die Informationen zurückgegeben werden. *TableName* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @rowguid = ] rowguid`Ist der eindeutige Bezeichner der Zeile. *ROWGUID* ist vom Datentyp **uniqueidentifier**und hat keinen Standardwert.  
  
`[ @show = ] 'show'`Bestimmt die Menge der Informationen, die im Resultset zurückgegeben werden sollen. *Show* ist vom Datentyp **nvarchar (20)** . der Standardwert ist Both. Wenn **Row**, werden nur Zeilen Versionsinformationen zurückgegeben. Wenn **Spalten**, werden nur Spalten Versionsinformationen zurückgegeben. Wenn **beides**, werden sowohl Zeilen-als auch Spalten Informationen zurückgegeben.  
  
## <a name="result-sets-for-row-information"></a>Resultsets für Zeileninformationen  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**server_name**|**sysname**|Name des Servers mit der Datenbank, in der der Eintrag der Zeilenversion vorgenommen wurde.|  
|**db_name**|**sysname**|Name der Datenbank, in der dieser Eintrag vorgenommen wurde.|  
|**db_nickname**|**Binary (6)**|Spitzname der Datenbank, in der dieser Eintrag vorgenommen wurde.|  
|**version**|**int**|Version des Eintrags.|  
|**current_state**|**nvarchar (9)**|Gibt Informationen zum aktuellen Status der Zeile zurück.<br /><br /> **y** -Zeilendaten stellt den aktuellen Status der Zeile dar.<br /><br /> **n** -Zeilendaten stellen nicht den aktuellen Status der Zeile dar.<br /><br /> nicht zutreffend>: nicht zutreffend. ** \<**<br /><br /> Unbekannter>-aktueller Status kann nicht bestimmt werden. ** \<**|  
|**rowversion_table**|**NCHAR (17)**|Gibt an, ob die Zeilen Versionen in der [MSmerge_contents](../../relational-databases/system-tables/msmerge-contents-transact-sql.md) Tabelle oder der [MSmerge_tombstone](../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md) Tabelle gespeichert werden.|  
|**geäußert**|**nvarchar(255)**|Zusätzliche Informationen zu diesem Zeilenversionseintrag. Normalerweise ist dieses Feld leer.|  
  
## <a name="result-sets-for-column-information"></a>Resultsets für Spalteninformationen  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**server_name**|**sysname**|Name des Servers mit der Datenbank, in der Eintrag der Spaltenversion vorgenommen wurde.|  
|**db_name**|**sysname**|Name der Datenbank, in der dieser Eintrag vorgenommen wurde.|  
|**db_nickname**|**Binary (6)**|Spitzname der Datenbank, in der dieser Eintrag vorgenommen wurde.|  
|**version**|**int**|Version des Eintrags.|  
|**ColName**|**sysname**|Name der Artikelspalte, die der Eintrag der Spaltenversion darstellt.|  
|**geäußert**|**nvarchar(255)**|Zusätzliche Informationen zu diesem Spaltenversionseintrag. Normalerweise ist dieses Feld leer.|  
  
## <a name="result-set-for-both"></a>Resultset für beide  
 Wenn **der Wert für** " *anzeigen*" ausgewählt ist, werden die Resultsets für Zeilen und Spalten zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_showrowreplicainfo** wird bei der Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 **sp_showrowreplicainfo** können nur von Mitgliedern der **db_owner** Fixed-Daten Bank Rolle in der Veröffentlichungs Datenbank oder von Mitgliedern der Veröffentlichungs Zugriffsliste (Publication Access List, PAL) in der Veröffentlichungs Datenbank ausgeführt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erkennen und Auflösen von mergereplikationskonflikten](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
