---
title: sys. sp_cdc_generate_wrapper_function (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cdc_generate_wrapper_function_TSQL
- sp_cdc_generate_wrapper_function
- sys.sp_cdc_generate_wrapper_function_TSQL
- sys.sp_cdc_generate_wrapper_function
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_cdc_generate_wrapper_function
- sp_cdc_generate_wrapper_function
ms.assetid: 85bc086d-8a4e-4949-a23b-bf53044b925c
author: rothja
ms.author: jroth
ms.openlocfilehash: 074e114f81db6615a04240f10447a3f711a51cf7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68083753"
---
# <a name="syssp_cdc_generate_wrapper_function-transact-sql"></a>sys.sp_cdc_generate_wrapper_function (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Generiert Skripts zur Erstellung von Wrapperfunktionen für die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verfügbaren Change Data Capture-Abfragefunktionen. Die in den generierten Wrappern unterstützte API ermöglicht die Angabe des Abfrageintervalls als datetime-Intervall. Aus diesem Grund eignet sich die Funktion ideal in vielen Warehousinganwendungen, einschließlich der Anwendungen, die von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Paketdesignern entwickelt werden, die Change Data Capture-Technologie zur Bestimmung inkrementeller Ladevorgänge verwenden.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.sp_cdc_generate_wrapper_function  
    [ [ @capture_instance sysname = ] 'capture_instance'  
    [ , [ @closed_high_end_point = ] closed_high_end_pt  
    [ , [ @column_list = ] 'column_list'  
```  
  
```  
  
[ , [ @update_flag_list = ] 'update_flag_list'  
```  
  
## <a name="arguments"></a>Argumente  
 [ @capture_instance= ] "*capture_instance*"  
 Die Aufzeichnungsinstanz, für die Skripts generiert werden sollen. *capture_instance* ist vom **Datentyp vom Datentyp sysname** und hat den Standardwert NULL. Wenn ein Wert weggelassen oder explizit auf NULL gesetzt wird, werden Wrapperskripts für alle Aufzeichnungsinstanzen generiert.  
  
 [ @closed_high_end_point= ] *high_end_pt_flag*  
 Das Flagbit, das angibt, ob Änderungen, deren Commitzeit gleich dem oberen Endpunkt ist, von der generierten Prozedur innerhalb des Extrahierungsintervalls eingeschlossen werden sollen. *high_end_pt_flag* ist vom Typ **Bit** und hat den Standardwert 1. Dies bedeutet, dass der Endpunkt eingeschlossen werden muss. Ein Wert von 0 gibt an, dass alle Commitzeiten unter dem oberen Endpunkt liegen müssen.  
  
 [ @column_list= ] "*column_list*"  
 Eine Liste erfasster Spalten, die in das Resultset eingeschlossen werden sollen, das von der Wrapperfunktion zurückgegeben wird. *column_list* ist vom Datentyp **nvarchar (max)** und hat den Standardwert NULL. Bei Angabe von NULL werden alle aufgezeichneten Spalten eingeschlossen.  
  
 [ @update_flag_list= ] "*update_flag_list*"  
 Eine Liste enthaltener Spalten, für die das von der Wrapperfunktion zurückgegebene Resultset ein Updateflag enthält. *update_flag_list* ist vom Datentyp **nvarchar (max)** und hat den Standardwert NULL. Bei Angabe von NULL werden keine Updateflags eingeschlossen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Spaltentyp|Beschreibung|  
|-----------------|-----------------|-----------------|  
|**function_name**|**nvarchar (145)**|Name der generierten Funktion.|  
|**create_script**|**nvarchar(max)**|Das Skript, mit dem die Wrapperfunktion der Aufzeichnungsinstanz erstellt wird.|  
  
## <a name="remarks"></a>Bemerkungen  
 Das Skript zur Erstellung der Wrapperfunktion für eine Abfrage aller Änderungen für eine Aufzeichnungsinstanz wird immer generiert. Wenn die Aufzeichnungsinstanz Abfragen für Nettoänderungen unterstützt, wird auch das Skript zur Generierung einer Wrapperfunktion für diese Abfrage generiert1.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel zeigt, wie Sie mit `sys.sp_cdc_generate_wrapper_function` Wrapper für alle Change Data Capture-Funktionen erstellen.  
  
```  
DECLARE @wrapper_functions TABLE (  
    function_name sysname,  
    create_script nvarchar(max));  
  
INSERT INTO @wrapper_functions  
EXEC sys.sp_cdc_generate_wrapper_function;  
  
DECLARE @create_script nvarchar(max);  
DECLARE #hfunctions CURSOR LOCAL fast_forward  
FOR   
    SELECT create_script FROM @wrapper_functions;  
  
OPEN #hfunctions;  
FETCH #hfunctions INTO @create_script;  
WHILE (@@fetch_status <> -1)  
BEGIN  
    EXEC sp_executesql @create_script  
    FETCH #hfunctions INTO @create_script  
END;  
  
CLOSE #hfunctions;  
DEALLOCATE #hfunctions;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Prozeduren für Change Data Capture &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/change-data-capture-stored-procedures-transact-sql.md)   
 [Change Data Capture &#40;SSIS-&#41;](../../integration-services/change-data-capture/change-data-capture-ssis.md)  
  
  
