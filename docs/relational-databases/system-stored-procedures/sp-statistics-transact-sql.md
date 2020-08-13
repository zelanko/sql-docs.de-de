---
title: sp_statistics (Transact-SQL) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 34d4b7763fd35b2012a90240a4d27fa27018f828
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2020
ms.locfileid: "88173100"
---
# <a name="sp_statistics-transact-sql"></a>sp_statistics (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Gibt eine Liste mit allen Indizes und Statistiken einer angegebenen Tabelle oder indizierten Sicht zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
sp_statistics [ @table_name = ] 'table_name'    
     [ , [ @table_owner = ] 'owner' ]   
     [ , [ @table_qualifier = ] 'qualifier' ]   
     [ , [ @index_name = ] 'index_name' ]   
     [ , [ @is_unique = ] 'is_unique' ]  
     [ , [ @accuracy = ] 'accuracy' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @table_name = ] 'table_name'`Gibt die Tabelle an, mit der Katalog Informationen zurückgegeben werden. *table_name* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Mustervergleiche mit Platzhalterzeichen werden nicht unterstützt.  
  
`[ @table_owner = ] 'owner'`Der Name des Tabellen Besitzers der Tabelle, die zum Zurückgeben von Katalog Informationen verwendet wird. *TABLE_OWNER* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Mustervergleiche mit Platzhalterzeichen werden nicht unterstützt. Wenn *Owner* nicht angegeben wird, werden die Standardregeln für die Tabellen Sichtbarkeit des zugrunde liegenden DBMS angewendet.  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden die Indizes einer Tabelle zurückgegeben, wenn der aktuelle Benutzer diese Tabelle mit dem angegebenen Namen besitzt. Wenn *Owner* nicht angegeben wird und der aktuelle Benutzer keine Tabelle mit dem angegebenen *Namen*besitzt, sucht diese Prozedur nach einer Tabelle mit dem angegebenen *Namen* , die im Besitz des Daten Bank Besitzers ist. Sofern eine solche Tabelle vorhanden ist, werden die Indizes dieser Tabelle zurückgegeben.  
  
`[ @table_qualifier = ] 'qualifier'`Der Name des Tabellen Qualifizierers. *qualifier* ist vom Datentyp **sysname**und hat den Standardwert NULL. Verschiedene DBMS-Produkte unterstützen eine dreiteilige Benennung für Tabellen (_Qualifizierer_)**.** _Besitzer_**.** _Name_). In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] entspricht dieser Parameter dem Datenbanknamen. Bei anderen Produkten stellt sie den Servernamen der Datenbankumgebung für die Tabelle dar.  
  
`[ @index_name = ] 'index_name'`Der Indexname. *index_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert%. Mustervergleiche mit Platzhalterzeichen werden unterstützt.  
  
`[ @is_unique = ] 'is_unique'`Gibt an, ob nur eindeutige Indizes (wenn **Y**) zurückgegeben werden sollen. *is_unique* ist vom Typ **char (1)** und hat den Standardwert **N**.  
  
`[ @accuracy = ] 'accuracy'`Die Ebene der Kardinalität und Seiten Genauigkeit für Statistiken. die *Genauigkeit* ist " **char (1)**". der Standardwert ist " **Q**". Geben Sie **E** an, um sicherzustellen, dass die Statistiken aktualisiert werden, sodass Kardinalität und Seiten korrekt sind.  
  
 Der Wert **E** (SQL_ENSURE) fordert den Treiber auf, die Statistiken bedingungslos abzurufen.  
  
 Der Wert **Q** (SQL_QUICK) fordert den Treiber auf, die Kardinalität und Seiten nur abzurufen, wenn Sie auf dem Server sofort verfügbar sind. In diesem Fall wird vom Treiber nicht sichergestellt, dass die Werte aktuell sind. Anwendungen, die nach dem "Open Group"-Standard geschrieben wurden, rufen immer das SQL_QUICK-Verhalten von Treibern ab, die mit ODBC 3.x kompatibel sind.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**TABLE_QUALIFIER**|**sysname**|Tabellen qualifizierername. Diese Spalte kann NULL enthalten.|  
|**TABLE_OWNER**|**sysname**|Der Name des Tabellen Besitzers. Diese Spalte gibt immer einen Wert zurück.|  
|**TABLE_NAME**|**sysname**|Tabellenname. Diese Spalte gibt immer einen Wert zurück.|  
|**NON_UNIQUE**|**smallint**|nicht NULL.<br /><br /> 0 = Eindeutig<br /><br /> 1 = Nicht eindeutig|  
|**INDEX_QUALIFIER**|**sysname**|Der Name des Index Besitzers. Verschiedene DBMS-Produkte ermöglichen neben dem Tabellenbesitzer auch anderen Benutzern das Erstellen von Indizes. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist diese Spalte immer identisch mit **table_name**.|  
|**INDEX_NAME**|**sysname**|Der Name des Indexes. Diese Spalte gibt immer einen Wert zurück.|  
|**TYPE**|**smallint**|Diese Spalte gibt immer einen Wert zurück:<br /><br /> 0 = Statistiken für eine Tabelle<br /><br /> 1 = In einem Cluster gruppiert<br /><br /> 2 = Hash<br /><br /> 3 = nicht gruppiert|  
|**SEQ_IN_INDEX**|**smallint**|Position der Spalte im Index|  
|**COLUMN_NAME**|**sysname**|Der Spaltenname für jede Spalte der zurückgegebenen **table_name** . Diese Spalte gibt immer einen Wert zurück.|  
|**Sortierung**|**char (1)**|Die in der Sortierung verwendete Reihenfolge. Mögliche Werte sind:<br /><br /> A = Aufsteigend<br /><br /> D = Absteigend<br /><br /> NULL = Nicht zutreffend|  
|**Kardinalität**|**int**|Anzahl der Zeilen in der Tabelle oder der eindeutigen Werte im Index|  
|**Seiten**|**int**|Anzahl der Seiten, die zum Speichern des Indexes oder der Tabelle benötigt werden|  
|**FILTER_CONDITION**|**varchar(128)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt keinen Wert zurück.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Die Indizes im Resultset werden in aufsteigender Reihenfolge nach den Spalten **NON_UNIQUE**, **Type**, **index_name**und **SEQ_IN_INDEX**angezeigt.  
  
 Die Indexart Gruppiert bezeichnet einen Index, der sich dadurch auszeichnet, dass die in der Tabelle gespeicherten Daten in der durch den Index vorgegebenen Reihenfolge abgelegt sind. Dies entspricht [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gruppierten Indizes.  
  
 Beim Indextyp Hash ist die Suche nach genauen Übereinstimmungen oder Wertebereichen zwar zulässig, bei Mustervergleichen wird der Index jedoch nicht verwendet.  
  
 **sp_statistics** entspricht **SQLStatistics** in ODBC. Die zurückgegebenen Ergebnisse werden nach **NON_UNIQUE**, **Typ**, **INDEX_QUALIFIER**, **index_name**und **SEQ_IN_INDEX**geordnet. Weitere Informationen finden Sie in der [ODBC-API-Referenz](https://go.microsoft.com/fwlink/?LinkId=68323).  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert SELECT-Berechtigung für das Schema.  
  
## <a name="example-sssdwfull-and-sspdw"></a>Beispiel: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Im folgenden Beispiel werden Informationen über die-Tabelle zurückgegeben `DimEmployee` .  
  
```sql  
-- Uses AdventureWorks  
  
EXEC sp_statistics DimEmployee;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Katalog Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

