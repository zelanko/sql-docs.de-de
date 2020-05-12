---
title: TYPE_ID (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- TYPE_ID
- TYPE_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IDs [SQL Server], types
- TYPE_ID function
- type IDs [SQL Server]
- data types [SQL Server], IDs
ms.assetid: 647d17ef-b878-4922-b446-56642322ebad
author: julieMSFT
ms.author: jrasnick
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a685df58164169f269069b92665cc6d446459e87
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82832794"
---
# <a name="type_id-transact-sql"></a>TYPE_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt die ID für einen angegebenen Datentypnamen zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
TYPE_ID ( [ schema_name ] type_name )   
```  
  
## <a name="arguments"></a>Argumente  
 *type_name*  
 Der Name des Datentyps. *type_name* ist vom Typ **nvarchar**. *type_name* kann ein Systemdatentyp oder benutzerdefinierter Datentyp sein.  
  
## <a name="return-types"></a>Rückgabetypen  
 **int**  
  
## <a name="exceptions"></a>Ausnahmen  
 Gibt NULL bei einem Fehler zurück oder wenn ein Aufrufer nicht über Berechtigungen zum Anzeigen des Objekts verfügt.  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann ein Benutzer nur die Metadaten sicherungsfähiger Elemente anzeigen, bei denen der Benutzer entweder der Besitzer ist oder für die dem Benutzer eine Berechtigung erteilt wurde. Dies bedeutet, dass Metadaten ausgebende integrierte Funktionen, z. B. TYPE_ID, möglicherweise NULL zurückgeben, wenn dem Benutzer für das Objekt keine Berechtigung erteilt wurde. Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="remarks"></a>Bemerkungen  
 TYPE_ID gibt NULL zurück, wenn der Datentypname ungültig ist, oder wenn der Benutzer nicht die erforderliche Berechtigung besitzt, um den Datentyp zu verwenden.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-looking-up-the-type-id-values-for-single--and-two-part-type-names"></a>A. Suchen der TYPE ID-Werte für aus ein oder zwei Teilen bestehende Typnamen  
 Im folgenden Beispiel wird die Datentyp-ID für ein- und zweiteilige Datentypnamen zurückgegeben.  
  
```  
USE tempdb;  
GO  
CREATE TYPE NewType FROM int;  
GO  
CREATE SCHEMA NewSchema;  
GO  
CREATE TYPE NewSchema.NewType FROM int;  
GO  
SELECT TYPE_ID('NewType') AS [1 Part Data Type ID],  
       TYPE_ID('NewSchema.NewType') AS [2 Part Data Type ID];  
GO  
```  
  
### <a name="b-looking-up-the-type-id-of-a-system-data-type"></a>B. Suchen der TYPE ID eines Systemdatentyps  
 Im folgenden Beispiel wird die `TYPE ID` für den `datetime`-Systemdatentyp zurückgegeben.  
  
```  
SELECT TYPE_NAME(TYPE_ID('datetime')) AS [TYPE_NAME]  
    ,TYPE_ID('datetime') AS [TYPE_ID];  
GO  
```  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-looking-up-the-type-id-of-a-system-data-type"></a>C: Abrufen des TYPE ID-Werts eines Systemdatentyps  
 Im folgenden Beispiel wird die `TYPE ID` für den `datetime`-Systemdatentyp zurückgegeben.  
  
```  
SELECT TYPE_NAME(TYPE_ID('datetime')) AS typeName,   
    TYPE_ID('datetime') AS typeID FROM table1;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [TYPE_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/type-name-transact-sql.md)   
 [TYPEPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/typeproperty-transact-sql.md)   
 [sys.types &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)   
 [Metadata Functions &#40;Transact-SQL&#41; (Metadatenfunktionen (Transact-SQL))](../../t-sql/functions/metadata-functions-transact-sql.md)  
  
  

