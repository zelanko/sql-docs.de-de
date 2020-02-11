---
title: sys. dm_tran_top_version_generators (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_tran_top_version_generators
- sys.dm_tran_top_version_generators
- dm_tran_top_version_generators_TSQL
- sys.dm_tran_top_version_generators_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_tran_top_version_generators dynamic management view
ms.assetid: cec7809b-ba8a-4df9-b5bb-d4f651ff1a86
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e8fb59e9cfe636f6cab775fa2cb000c60ba08ad2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68262609"
---
# <a name="sysdm_tran_top_version_generators-transact-sql"></a>sys.dm_tran_top_version_generators (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt eine virtuelle Tabelle für die Objekte zurück, die die meisten Versionen im Versionsspeicher erzeugen. **sys. dm_tran_top_version_generators** gibt die obersten 256 aggregierten Daten Satzlängen zurück, die nach **database_id** und **rowset_id**gruppiert sind. **sys. dm_tran_top_version_generators** Ruft Daten ab, indem die **dm_tran_version_store** virtuelle Tabelle abgefragt wird. **sys. dm_tran_top_version_generators** ist eine ineffiziente Sicht, die ausgeführt werden kann, da in dieser Ansicht der Versionsspeicher abgefragt wird und der Versionsspeicher sehr groß sein kann. Die Verwendung dieser Funktion wird empfohlen, um die größten Consumer des Versionsspeichers zu suchen.  
  
> [!NOTE]  
>  Um dies von oder [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]aus aufzurufen, verwenden Sie den Namen **sys. dm_pdw_nodes_tran_top_version_generators**.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.dm_tran_top_version_generators  
```  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|Datenbank-ID|  
|**rowset_id**|**BIGINT**|Rowset-ID.|  
|**aggregated_record_length_in_bytes**|**int**|Summe der Daten Satzlängen der einzelnen **database_id** und **rowset_id Paars** im Versionsspeicher.|  
|**pdw_node_id**|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Der Bezeichner für den Knoten, auf dem sich diese Distribution befindet.|  
  
## <a name="permissions"></a>Berechtigungen

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]ist die `VIEW SERVER STATE` -Berechtigung erforderlich.   
Bei [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium-Tarifen ist die `VIEW DATABASE STATE` -Berechtigung in der Datenbank erforderlich. In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] den Tarifen "Standard" und "Basic" ist der **Server Administrator** oder ein **Azure Active Directory Administrator** Konto erforderlich.   

## <a name="remarks"></a>Bemerkungen  
 Da **sys. dm_tran_top_version_generators** möglicherweise viele Seiten lesen muss, während Sie den gesamten Versionsspeicher scannt, kann die Ausführung von **sys. dm_tran_top_version_generators** die Systemleistung beeinträchtigen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird ein Testszenario verwendet, in dem vier gleichzeitige Transaktionen, die jeweils durch eine Transaktionssequenznummer (XSN) identifiziert werden, in einer Datenbank ausgeführt werden, für die die Optionen ALLOW_SNAPSHOT_ISOLATION und READ_COMMITTED_SNAPSHOT auf ON festgelegt sind. Die folgenden Transaktionen werden ausgeführt:  
  
-   XSN-57 ist ein Updatevorgang auf der serialisierbaren Isolationsstufe.  
  
-   XSN-58 entspricht XSN-57.  
  
-   XSN-59 ist ein Select-Vorgang auf der Momentaufnahmeisolationsstufe.  
  
-   XSN-60 entspricht XSN-59.  
  
 Die folgende Abfrage wird ausgeführt.  
  
```  
SELECT  
    database_id,  
    rowset_id,  
    aggregated_record_length_in_bytes  
  FROM sys.dm_tran_top_version_generators;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
database_id rowset_id            aggregated_record_length_in_bytes  
----------- -------------------- ---------------------------------  
9           72057594038321152    87  
9           72057594038386688    33  
```  
  
 Die Ausgabe zeigt, dass alle Versionen von `database_id``9` erstellt werden und dass die Versionen aus zwei Tabellen generiert werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungssichten und Funktionen in Verbindung mit Transaktionen &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


