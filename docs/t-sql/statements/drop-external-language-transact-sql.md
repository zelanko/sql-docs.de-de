---
title: DROP EXTERNAL LANGUAGE (Transact-SQL) – SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/08/2019
ms.prod: sql
ms.technology: language-extensions
ms.topic: language-reference
author: nelgson
ms.author: negust
ms.reviewer: dphansen
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6f4b6ee38ed70da600ef007f168cd7e95a010278
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85766369"
---
# <a name="drop-external-library-transact-sql"></a>DROP EXTERNAL LIBRARY (Transact-SQL)  
[!INCLUDE[SQL Server 2019](../../includes/applies-to-version/sqlserver2019.md)]

Löscht eine vorhandene externe Sprache.

## <a name="syntax"></a>Syntax

```text
DROP EXTERNAL LANGUAGE <language_name>
```

### <a name="arguments"></a>Argumente

**language_name**

Sprachen sind datenbankweite Objekte. Sprachnamen müssen innerhalb der Datenbank eindeutig sein.

## <a name="permissions"></a>Berechtigungen

Zum Löschen einer Sprache ist die Berechtigung ALTER ANY EXTERNAL LANGUAGE erforderlich. Standardmäßig kann jeder Datenbankbesitzer oder der Besitzer des Objekts auch eine externe Sprache löschen.

> [!NOTE]
> Beachten Sie, dass vor dem Entfernen einer externen Sprache die externen Bibliotheken entfernt werden müssen, die auf die externe Sprache verweisen.

### <a name="return-values"></a>Rückgabewerte

Eine Informationsmeldung wird zurückgegeben, wenn die Anweisung erfolgreich war.

## <a name="remarks"></a>Bemerkungen

Bevor eine externe Sprache gelöscht werden kann, müssen alle externen Bibliotheken für die angegebene Sprache gelöscht werden.

## <a name="examples"></a>Beispiele

Erstellen der externen Sprache **Java**:

```sql
CREATE EXTERNAL LANGUAGE Java 
FROM (CONTENT = N'<path-to-zip>', FILE_NAME = 'javaextension.dll');
GO
```

Löschen der externen Sprache:

```sql
DROP EXTERNAL LANGUAGE Java;
```

## <a name="see-also"></a>Weitere Informationen

[CREATE EXTERNAL LANGUAGE (Transact-SQL)](create-external-language-transact-sql.md)  
[ALTER EXTERNAL LANGUAGE (Transact-SQL)](alter-external-language-transact-sql.md)  
[sys.external_languages](../../relational-databases/system-catalog-views/sys-external-languages-transact-sql.md)  
[sys.external_language_files](../../relational-databases/system-catalog-views/sys-external-language-files-transact-sql.md)  
