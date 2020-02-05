---
title: FILEPROPERTY (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- FILEPROPERTY_TSQL
- FILEPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- viewing file properties
- names [SQL Server], files
- displaying file properties
- file properties [SQL Server]
- FILEPROPERTY function
- file names [SQL Server], FILEPROPERTY
ms.assetid: b82244ed-d623-431f-aa06-8017349d847f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 79be8af32c13b9e910b94b40bd3c1bf9b2c0e2c5
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "68071399"
---
# <a name="fileproperty-transact-sql"></a>FILEPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt den Eigenschaftswert für den angegebenen Dateinamen zurück, wenn ein Dateiname in der aktuellen Datenbank und ein Eigenschaftsname angegeben sind. Gibt NULL für Dateien zurück, die nicht in der aktuellen Datenbank sind.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
FILEPROPERTY ( file_name , property )  
```  
  
## <a name="arguments"></a>Argumente  
 *file_name*  
 Ein Ausdruck, der den Namen der Datei enthält, die der aktuellen Datenbank zugeordnet ist, für die Eigenschaftsinformationen zurückgegeben werden sollen. *file_name* ist vom Datentyp **nchar(128)** .  
  
 *property*  
 Ein Ausdruck, der den Namen der zurückzugebenden Dateieigenschaft enthält. *property* ist vom Datentyp **varchar(128)** . Die folgenden Werte sind möglich.  
  
|value|BESCHREIBUNG|Zurückgegebener Wert|  
|-----------|-----------------|--------------------|  
|**IsReadOnly**|Dateigruppe ist schreibgeschützt.|1 = True<br /><br /> 0 = False<br /><br /> NULL = Eingabe ist nicht gültig.|  
|**IsPrimaryFile**|Datei ist die primäre Datei.|1 = True<br /><br /> 0 = False<br /><br /> NULL = Eingabe ist nicht gültig.|  
|**IsLogFile**|Datei ist eine Protokolldatei.|1 = True<br /><br /> 0 = False<br /><br /> NULL = Eingabe ist nicht gültig.|  
|**SpaceUsed**|Speicherplatz, der von der angegebenen Datei verwendet wird.|Anzahl der in der Datei zugeordneten Seiten.|  
  
## <a name="return-types"></a>Rückgabetypen  
 **int**  
  
## <a name="remarks"></a>Bemerkungen  
 *file_name* entspricht der **name**-Spalte in den Katalogsichten **sys.master_files** oder **sys.database_files**.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Einstellung für die `IsPrimaryFile`-Eigenschaft des `AdventureWorks_Data`-Dateinamens in der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]-Datenbank zurückgegeben.  
  
```  
  
SELECT FILEPROPERTY('AdventureWorks2012_Data', 'IsPrimaryFile')AS [Primary File];  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Primary File   
-------------  
1  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [FILEGROUPPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/filegroupproperty-transact-sql.md)   
 [Metadata Functions &#40;Transact-SQL&#41; (Metadatenfunktionen &#40;Transact-SQL&#41;)](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sp_spaceused &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
  
