---
description: IS_OBJECTSIGNED (Transact-SQL)
title: IS_OBJECTSIGNED (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- IS_OBJECTSIGNED
- IS_OBJECTSIGNED_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IS_OBJECTSIGNED function
ms.assetid: afbc4f7f-8266-4ee6-9802-14a2dbe69ef6
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: e6ef80c95e7ff6fb2751a86d10ea707b2a1033d5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88422714"
---
# <a name="is_objectsigned-transact-sql"></a>IS_OBJECTSIGNED (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Gibt an, ob ein Objekt von einem angegebenen Zertifikat oder asymmetrischen Schlüssel signiert wird.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
IS_OBJECTSIGNED (   
'OBJECT', @object_id, @class, @thumbprint  
  )   
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 **'OBJECT'**  
 Der Typ der sicherbaren Klasse.  
  
 *\@object_id*  
 Die object_id des Objekts, das getestet wird. *\@object_id* weist den Typ **int** auf.  
  
 *\@class*  
 Klasse des Objekts:  
  
-   ‚Zertifikat’  
  
-   ‚asymmetrischer Schlüssel’  
  
 *\@class* weist den Typ **sysname** auf.  
  
 *\@thumbprint*  
 Der SHA-Fingerabdruck des Objekts. *\@thumbprint* hat den Datentyp **varbinary(32)** .  
  
## <a name="returned-types"></a>Rückgabetypen  
 **int**  
  
## <a name="remarks"></a>Bemerkungen  
 IS_OBJECTSIGNED gibt folgende Werte zurück.  
  
|Rückgabewert|BESCHREIBUNG|  
|------------------|-----------------|  
|NULL|Das Objekt wurde nicht signiert oder ist nicht gültig.|  
|0|Das Objekt wurde signiert, die Signatur ist jedoch nicht gültig.|  
|1|Das Objekt ist signiert.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW DEFINITION-Berechtigung für das Zertifikat oder den asymmetrischen Schlüssel.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-displaying-extended-properties-on-a-database"></a>A. Anzeigen erweiterter Eigenschaften für eine Datenbank  
 Im folgenden Beispiel wird getestet, ob die Tabelle spt_fallback_db in der **master**-Datenbank vom Schemasignaturzertifikat signiert wird.  
  
```  
USE master;  
-- Declare a variable to hold a thumbprint and an object name  
DECLARE @thumbprint varbinary(20), @objectname sysname;  
  
-- Populate the thumbprint variable with the thumbprint of   
-- the master database schema signing certificate  
SELECT @thumbprint = thumbprint   
FROM sys.certificates   
WHERE name LIKE '%SchemaSigningCertificate%';  
  
-- Populate the object name variable with a table name in master  
SELECT @objectname = 'spt_fallback_db';  
  
-- Query to see if the table is signed by the thumbprint  
SELECT @objectname AS [object name],  
IS_OBJECTSIGNED(  
'OBJECT', OBJECT_ID(@objectname), 'certificate', @thumbprint  
) AS [Is the object signed?] ;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys.fn_check_object_signatures &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-check-object-signatures-transact-sql.md)  
  
  
