---
title: FILEGROUPPROPERTY (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5563c65352713f3557e4c412607d1944f28f3a3f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68071427"
---
# <a name="filegroupproperty-transact-sql"></a>FILEGROUPPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Diese Funktion gibt den filegroup-Eigenschaftenwert für einen angegebenen Namens- und Dateigruppenwert zurück.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
FILEGROUPPROPERTY ( filegroup_name, property )  
```  
  
## <a name="arguments"></a>Argumente  
 *filegroup_name*  
Ein Ausdruck vom Datentyp **sysname**, der den Namen der Dateigruppe darstellt, für die `FILEGROUPPROPERTY` die benannten Eigenschafteninformationen zurückgibt.  
  
 *property*  
Ein Ausdruck vom Typ **varchar(128)** , der den Namen der Dateigruppeneigenschaft zurückgibt. *property* kann einen dieser Werte zurückgeben:  
  
|value|und Beschreibung|Zurückgegebener Wert|  
|-----------|-----------------|--------------------|  
|**IsReadOnly**|Dateigruppe ist schreibgeschützt.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL: Ungültige Eingabe|  
|**IsUserDefinedFG**|Dateigruppe ist eine benutzerdefinierte Dateigruppe.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL: Ungültige Eingabe|  
|**IsDefault**|Dateigruppe ist die Standarddateigruppe.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL: Ungültige Eingabe|  
  
## <a name="return-types"></a>Rückgabetypen  
**int**  
  
## <a name="remarks"></a>Remarks  
*filegroup_name* entspricht der Spalte **name** der **sys.filegroups**-Katalogsicht.  
  
## <a name="examples"></a>Beispiele  
In diesem Beispiel wird die Einstellung der Eigenschaft `IsDefault` für die primäre Dateigruppe in der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]-Datenbank zurückgegeben.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [FILEGROUP_ID &#40;Transact-SQL&#41;](../../t-sql/functions/filegroup-id-transact-sql.md)   
 [FILEGROUP_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/filegroup-name-transact-sql.md)   
 [Metadata Functions &#40;Transact-SQL&#41; (Metadatenfunktionen &#40;Transact-SQL&#41;)](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [sys.filegroups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)  
  
  
