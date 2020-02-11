---
title: sys. sp_cdc_disable_table (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sp_cdc_disable_table
- sp_cdc_disable_table
- sys.sp_cdc_disable_table_TSQL
- sp_cdc_disable_table_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_disable_table
- sys.sp_cdc_disable_table
- change data capture [SQL Server], disabling tables
ms.assetid: da2156c0-504e-4d76-b9a0-4448becf9bda
author: rothja
ms.author: jroth
ms.openlocfilehash: 693c449679433b733cfc3a45e2bbedf3f1d92185
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68106510"
---
# <a name="syssp_cdc_disable_table-transact-sql"></a>sys.sp_cdc_disable_table (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Deaktiviert Change Data Capture für die angegebene Quelltabelle und die Aufzeichnungsinstanz in der aktuellen Datenbank. Change Data Capture ist nicht in jeder Edition von [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Eine Liste der Funktionen, die von den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Editionen unterstützt werden, finden Sie unter [Von den SQL Server 2016-Editionen unterstützte Funktionen](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.sp_cdc_disable_table   
  [ @source_schema = ] 'source_schema' ,   
  [ @source_name = ] 'source_name'  
  [ , [ @capture_instance = ] 'capture_instance' | 'all' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @source_schema = ] 'source\_schema'`Der Name des Schemas, in dem die Quell Tabelle enthalten ist. *source_schema* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert und darf nicht NULL sein.  
  
 *source_schema* muss in der aktuellen Datenbank vorhanden sein.  
  
`[ @source_name = ] 'source\_name'`Der Name der Quell Tabelle, aus der Change Data Capture deaktiviert werden soll. *source_name* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert und darf nicht NULL sein.  
  
 *source_name* muss in der aktuellen Datenbank vorhanden sein.  
  
`[ @capture_instance = ] 'capture\_instance' | 'all'`Der Name der Aufzeichnungs Instanz, die für die angegebene Quell Tabelle deaktiviert werden soll. *capture_instance* ist vom **Datentyp vom Datentyp sysname** und darf nicht NULL sein.  
  
 Wenn ' all ' angegeben ist, werden alle für *source_name* definierten Aufzeichnungs Instanzen deaktiviert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 **sys. sp_cdc_disable_table** löscht die Change Data Capture Änderungs Tabelle und die Systemfunktionen, die der angegebenen Quell Tabelle und der Aufzeichnungs Instanz zugeordnet sind. Dadurch werden alle Zeilen, die der angegebenen Aufzeichnungs Instanz zugeordnet sind, aus den Change Data Capture Systemtabellen gelöscht, und die **is_tracked_by_cdc** Spalte für den Tabelleneintrag in der [sys. Tables](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md) -Katalog Sicht wird auf 0 festgelegt.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **db_owner** Fixed-Daten Bank Rolle.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird Change Data Capture für die `HumanResources.Employee`-Tabelle deaktiviert.  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_disable_table   
    @source_schema = N'HumanResources',   
    @source_name = N'Employee',  
    @capture_instance = N'HumanResources_Employee';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys. sp_cdc_enable_table &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md)  
  
  
