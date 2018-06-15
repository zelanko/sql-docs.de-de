---
title: FILEGROUPPROPERTY (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- FILEGROUPPROPERTY_TSQL
- FILEGROUPPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- filegroups [SQL Server], property values
- FILEGROUPPROPERTY function
- viewing filegroup properties
- displaying filegroup properties
ms.assetid: b3a930e6-df05-4034-929c-f681f5f6fc6e
caps.latest.revision: 22
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 2c7e3b446216f521bbb0d885784db017edf2bcd5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "33054297"
---
# <a name="filegroupproperty-transact-sql"></a>FILEGROUPPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt den angegebenen Eigenschaftswert der Dateigruppe für bereitgestellte Dateigruppen- und Eigenschaftsnamen zurück.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
FILEGROUPPROPERTY ( filegroup_name , property )  
```  
  
## <a name="arguments"></a>Argumente  
 *filegroup_name*  
 Ein Ausdruck vom **sysname**-Datentyp, der den Namen der Dateigruppe darstellt, für die die benannte Eigenschaftsinformation zurückgegeben wird.  
  
 *property*  
 Ein Ausdruck vom Typ **varchar(128)**, der den Namen der Dateigruppeneigenschaft enthält, die zurückgegeben werden soll. *property* kann einen der folgenden Werte aufweisen.  
  
|value|Description|Zurückgegebener Wert|  
|-----------|-----------------|--------------------|  
|**IsReadOnly**|Dateigruppe ist schreibgeschützt.|1 = True<br /><br /> 0 = False<br /><br /> NULL = Eingabe ist nicht gültig.|  
|**IsUserDefinedFG**|Dateigruppe ist eine benutzerdefinierte Dateigruppe.|1 = True<br /><br /> 0 = False<br /><br /> NULL = Eingabe ist nicht gültig.|  
|**IsDefault**|Dateigruppe ist die Standarddateigruppe.|1 = True<br /><br /> 0 = False<br /><br /> NULL = Eingabe ist nicht gültig.|  
  
## <a name="return-types"></a>Rückgabetypen  
 **int**  
  
## <a name="remarks"></a>Remarks  
 *filegroup_name* entspricht der **name**-Spalte der **sys.filegroups**-Katalogsicht.  
  
## <a name="examples"></a>Beispiele  
 In diesem Beispiel wird die Einstellung für die `IsDefault`-Eigenschaft für die primäre Dateigruppe in der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]-Datenbank zurückgegeben.  
  
```  
  
SELECT FILEGROUPPROPERTY('PRIMARY', 'IsDefault') AS 'Default Filegroup';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Default Filegroup   
---------------------   
1  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [FILEGROUP_ID &#40;Transact-SQL&#41;](../../t-sql/functions/filegroup-id-transact-sql.md)   
 [FILEGROUP_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/filegroup-name-transact-sql.md)   
 [Metadata Functions &#40;Transact-SQL&#41; (Metadatenfunktionen &#40;Transact-SQL&#41;)](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [sys.filegroups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)  
  
  
