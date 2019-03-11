---
title: DROP EXTERNAL LIBRARY (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/28/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP EXTERNAL LIBRARY
- DROP_EXTERNAL_LIBRARY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DROP EXTERNAL LIBRARY
author: dphansen
ms.author: davidph
manager: cgronlund
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 129aafce2e270f85506d056d5d083d34176aa8a0
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/01/2019
ms.locfileid: "57018016"
---
# <a name="drop-external-library-transact-sql"></a>DROP EXTERNAL LIBRARY (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Löscht eine vorhandene Paketbibliothek. Paketbibliotheken werden von unterstützten externen Runtimes wie R, Python oder Java verwendet.

> [!NOTE]
> In SQL Server 2017 werden die R-Sprache und die Windows-Plattform unterstützt. R. Python und Java werden für die Windows-Plattform in SQL Server 2019 CTP 2.3 unterstützt. Die Unterstützung für Linux ist für ein späteres Release eingeplant.

## <a name="syntax"></a>Syntax

```sql
DROP EXTERNAL LIBRARY library_name
[ AUTHORIZATION owner_name ];
```

### <a name="arguments"></a>Argumente

**library_name**

Gibt den Namen einer vorhandenen Paketbibliothek an.

Bibliotheken umfassen nur den Benutzer. Bibliotheksnamen müssen innerhalb des Kontexts eines bestimmten Benutzers oder Besitzers eindeutig sein.

**owner_name**

Gibt den Namen eines Benutzers oder einer Rolle an, der oder die die externe Bibliothek besitzt.

Datenbankbesitzer können Bibliotheken löschen, die von anderen Benutzern erstellt wurden.

## <a name="permissions"></a>Berechtigungen

Zum Löschen einer Bibliothek ist die Berechtigung ALTER ANY EXTERNAL LIBRARY erforderlich. Standardmäßig kann jeder Datenbankbesitzer oder der Besitzer des Objekts auch eine externe Bibliothek löschen.

### <a name="return-values"></a>Rückgabewerte

Eine Informationsmeldung wird zurückgegeben, wenn die Anweisung erfolgreich war.

## <a name="remarks"></a>Remarks

Im Gegensatz zu anderen `DROP`-Anweisungen in SQL Server unterstützt diese Anweisung das Angeben einer optionalen Autorisierungsklausel. Dies ermöglicht einem **dbo** oder Benutzer mit der Rolle **db_owner**, eine Paketbibliothek zu löschen, die von einem normalen Benutzer in die Datenbank hochgeladen wurde.

## <a name="examples"></a>Beispiele

Hinzufügen des benutzerdefinierten R-Pakets `customPackage` zu einer Datenbank:

```sql
CREATE EXTERNAL LIBRARY customPackage 
FROM (CONTENT = 'C:\temp\customPackage_v1.1.zip')
WITH (LANGUAGE = 'R');
GO
```

Löschen der `customPackage`-Bibliothek:

```sql
DROP EXTERNAL LIBRARY customPackage;
```

## <a name="see-also"></a>Siehe auch

[CREATE EXTERNAL LIBRARY (Transact-SQL)](create-external-library-transact-sql.md)  
[ALTER EXTERNAL LIBRARY (Transact-SQL)](alter-external-library-transact-sql.md)  
[sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md)  

