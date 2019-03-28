---
title: Sp_statistics (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_statistics_TSQL
- sp_statistics
dev_langs:
- TSQL
helpviewer_keywords:
- sp_statistics
ms.assetid: 0bb6495f-258a-47ec-9f74-fd16671d23b8
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: fdf0984f172657ad45ee6da0a09de5e0e457b003
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58527682"
---
# <a name="spstatistics-transact-sql"></a>sp_statistics (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt eine Liste mit allen Indizes und Statistiken einer angegebenen Tabelle oder indizierten Sicht zurück.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
sp_statistics [ @table_name = ] 'table_name'    
     [ , [ @table_owner = ] 'owner' ]   
     [ , [ @table_qualifier = ] 'qualifier' ]   
     [ , [ @index_name = ] 'index_name' ]   
     [ , [ @is_unique = ] 'is_unique' ]  
     [ , [ @accuracy = ] 'accuracy' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @table_name = ] 'table_name'` Gibt die Tabelle verwendet, um Kataloginformationen zurückzugeben. *TABLE_NAME* ist **Sysname**, hat keinen Standardwert. Mustervergleiche mit Platzhalterzeichen werden nicht unterstützt.  
  
`[ @table_owner = ] 'owner'` Ist der Name des Besitzers der Tabelle der Tabelle zurückgeben von Kataloginformationen verwendet wird. *Table_owner* ist **Sysname**, hat den Standardwert NULL. Mustervergleiche mit Platzhalterzeichen werden nicht unterstützt. Wenn *Besitzer* nicht angegeben ist, gelten die Standardregeln für die Sichtbarkeit von Tabellen des zugrunde liegenden DBMS.  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden die Indizes einer Tabelle zurückgegeben, wenn der aktuelle Benutzer diese Tabelle mit dem angegebenen Namen besitzt. Wenn *Besitzer* nicht angegeben ist und der aktuelle Benutzer keine Tabelle mit den angegebenen *Namen*, sieht Sie dieses Verfahren für eine Tabelle mit dem angegebenen *Namen* im Besitz der Besitzer der Datenbank. Sofern eine solche Tabelle vorhanden ist, werden die Indizes dieser Tabelle zurückgegeben.  
  
`[ @table_qualifier = ] 'qualifier'` Ist der Name des Qualifizierers der Tabelle. *qualifier* ist vom Datentyp **sysname**und hat den Standardwert NULL. Verschiedene DBMS-Produkte unterstützen eine dreiteilige Namensgebung für Tabellen (_Qualifizierer_**.** _Besitzer_**.** _Namen_). In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] entspricht dieser Parameter dem Datenbanknamen. Bei anderen Produkten stellt sie den Servernamen der Datenbankumgebung für die Tabelle dar.  
  
`[ @index_name = ] 'index_name'` Ist der Name des Indexes an. *Index_name* ist **Sysname**, hat den Standardwert %. Mustervergleiche mit Platzhalterzeichen werden unterstützt.  
  
`[ @is_unique = ] 'is_unique'` Ist, ob nur eindeutige Indizes (Wenn **Y**) zurückgegeben werden sollen. *Is_unique* ist **char(1)**, hat den Standardwert **N**.  
  
`[ @accuracy = ] 'accuracy'` Ist die Ebene der Kardinalität und seitengenauigkeit für Statistiken. *Genauigkeit* ist **char(1)**, hat den Standardwert **Q**. Geben Sie **E** um sicherzustellen, dass die Statistiken aktualisiert werden, sodass Kardinalität und Seiten stimmen.  
  
 Der Wert **E** (SQL_ENSURE) weist den Treiber zum unbedingten Abrufen der Statistiken.  
  
 Der Wert **Q** (SQL_QUICK) weist den Treiber zum Abrufen der Kardinalität und Seiten nur dann, wenn sie direkt auf dem Server verfügbar sind. In diesem Fall wird vom Treiber nicht sichergestellt, dass die Werte aktuell sind. Anwendungen, die nach dem "Open Group"-Standard geschrieben wurden, rufen immer das SQL_QUICK-Verhalten von Treibern ab, die mit ODBC 3.x kompatibel sind.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_QUALIFIER**|**sysname**|Name des Qualifizierers Tabelle. Diese Spalte kann NULL enthalten.|  
|**TABLE_OWNER**|**sysname**|Name des Tabellenbesitzers. Diese Spalte gibt immer einen Wert zurück.|  
|**TABLE_NAME**|**sysname**|Tabellenname. Diese Spalte gibt immer einen Wert zurück.|  
|**NON_UNIQUE**|**smallint**|NICHT NULL IST.<br /><br /> 0 = Eindeutig<br /><br /> 1 = Nicht eindeutig|  
|**INDEX_QUALIFIER**|**sysname**|Der Name des Indexbesitzers. Verschiedene DBMS-Produkte ermöglichen neben dem Tabellenbesitzer auch anderen Benutzern das Erstellen von Indizes. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], diese Spalte ist immer identisch **TABLE_NAME**.|  
|**INDEX_NAME**|**sysname**|Der Name des Indexes. Diese Spalte gibt immer einen Wert zurück.|  
|**TYPE**|**smallint**|Diese Spalte gibt immer einen Wert zurück:<br /><br /> 0 = Statistiken für eine Tabelle<br /><br /> 1 = In einem Cluster gruppiert<br /><br /> 2 = Hash<br /><br /> 3 = nicht gruppiert|  
|**SEQ_IN_INDEX**|**smallint**|Position der Spalte im Index|  
|**COLUMN_NAME**|**sysname**|Name der Spalte für jede Spalte von der **TABLE_NAME** zurückgegeben. Diese Spalte gibt immer einen Wert zurück.|  
|**COLLATION**|**char(1)**|Die in der Sortierung verwendete Reihenfolge. Mögliche Werte sind:<br /><br /> A = Aufsteigend<br /><br /> D = Absteigend<br /><br /> NULL = Nicht zutreffend|  
|**KARDINALITÄT**|**int**|Anzahl der Zeilen in der Tabelle oder der eindeutigen Werte im Index|  
|**SEITEN**|**int**|Anzahl der Seiten, die zum Speichern des Indexes oder der Tabelle benötigt werden|  
|**FILTER_CONDITION**|**varchar(128)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt keinen Wert zurück.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 None  
  
## <a name="remarks"></a>Hinweise  
 Die Indizes im Resultset angezeigt werden, in aufsteigender Reihenfolge nach den Spalten **NON_UNIQUE**, **Typ**, **INDEX_NAME**, und **SEQ_IN_INDEX**.  
  
 Die Indexart Gruppiert bezeichnet einen Index, der sich dadurch auszeichnet, dass die in der Tabelle gespeicherten Daten in der durch den Index vorgegebenen Reihenfolge abgelegt sind. Dies entspricht [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gruppierte Indizes.  
  
 Beim Indextyp Hash ist die Suche nach genauen Übereinstimmungen oder Wertebereichen zwar zulässig, bei Mustervergleichen wird der Index jedoch nicht verwendet.  
  
 **Sp_statistics** entspricht **SQLStatistics** in ODBC. Die zurückgegebenen Ergebnisse sind sortiert nach **NON_UNIQUE**, **Typ**, **INDEX_QUALIFIER**, **INDEX_NAME**, und **SEQ_IN_ INDEX**. Weitere Informationen finden Sie unter den [ODBC-API-Referenz](https://go.microsoft.com/fwlink/?LinkId=68323).  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert SELECT-Berechtigung für das Schema.  
  
## <a name="example-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Beispiel: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Das folgende Beispiel gibt Informationen über die `DimEmployee` Tabelle.  
  
```  
-- Uses AdventureWorks  
  
EXEC sp_statistics DimEmployee;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Prozeduren für Kataloginformationen &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

