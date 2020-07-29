---
title: Java-Datentypen
titleSuffix: SQL Server Language Extensions
description: Ordnen Sie Java-Datentypen für Ein- und Ausgabedatenstrukturen und für Eingabeparameter für „sp_execute_external_script“ SQL Server zu.
author: dphansen
ms.author: davidph
ms.date: 11/05/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 26c5e6f344d9fb0a14a21fa195214c4460673de0
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85748512"
---
# <a name="java-and-sql-server-supported-data-types"></a>Von Java und SQL Server unterstützte Datentypen
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

In diesem Artikel werden SQL Server-Datentypen für Datenstrukturen und Parameter für [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) Java-Datentypen zugeordnet.

Die folgenden SQL- und Java-Datentypen werden derzeit für Eingabe-/Ausgabedatasets und Eingabe-/Ausgabeparameter unterstützt.

| SQL-Datentyp        | Java-Datentyp | Comment | |
| ------------- |-------------|-|-|
| bit      | boolean | | |
| Tinyint      | short      | | |
| Smallint | short      | | |
| Int | INT      | | |
| Real | float      | | |
| Bigint | long      | | |
| float | double      | | |
| nchar(n) | String      | | |
| nvarchar(n) | String      | | |
| binary(n) | byte[]      | | |
| varbinary(n) | byte[]      | | |
| nvarchar(max) | String      | | |
| varbinary(max) | byte[]      | | |
| UNIQUEIDENTIFIER | String | | |
| char(n) | String | Nur UTF8-Zeichenfolgen werden unterstützt. | |
| varchar(n) | String | Nur UTF8-Zeichenfolgen werden unterstützt. | |
| varchar(max) | String | Nur UTF8-Zeichenfolgen werden unterstützt. | |
| date | java.sql.date  | | |
| NUMERIC | java.math.BigDecimal  | | |
| Decimal | java.math.BigDecimal  | | |
| money | java.math.BigDecimal  | | |
| SMALLMONEY | java.math.BigDecimal  | | |
| smalldatetime | java.sql.timestamp  | | |
| datetime | java.sql.timestamp  | | |
| datetime2 | java.sql.timestamp  | | |


## <a name="next-steps"></a>Nächste Schritte

+ [Aufrufen von Java in SQL Server](../how-to/call-java-from-sql.md)
