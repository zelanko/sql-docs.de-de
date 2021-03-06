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
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15'
ms.openlocfilehash: d5703470849f627cca87c471ea666b7c1b0e7e85
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97471741"
---
# <a name="java-and-sql-server-supported-data-types"></a>Von Java und SQL Server unterstützte Datentypen
[!INCLUDE [SQL Server 2019 and later](../../includes/applies-to-version/sqlserver2019.md)]

In diesem Artikel werden SQL Server-Datentypen für Datenstrukturen und Parameter für [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) Java-Datentypen zugeordnet.

Die folgenden SQL- und Java-Datentypen werden derzeit für Eingabe-/Ausgabedatasets und Eingabe-/Ausgabeparameter unterstützt.

| SQL-Datentyp        | Java-Datentyp | Comment |
| ------------- |-------------|-|
| bit      | boolean | |
| Tinyint      | short      | |
| Smallint | short      | |
| Int | INT      | |
| Real | float      | |
| Bigint | long      | |
| float | double      | |
| nchar(n) | String      | |
| nvarchar(n) | String      | |
| binary(n) | byte[]      | |
| varbinary(n) | byte[]      | |
| nvarchar(max) | String      | |
| varbinary(max) | byte[]      | |
| UNIQUEIDENTIFIER | String | |
| char(n) | String | Nur UTF8-Zeichenfolgen werden unterstützt. |
| varchar(n) | String | Nur UTF8-Zeichenfolgen werden unterstützt. |
| varchar(max) | String | Nur UTF8-Zeichenfolgen werden unterstützt. |
| date | java.sql.date  | |
| NUMERIC | java.math.BigDecimal  | |
| Decimal | java.math.BigDecimal  | |
| money | java.math.BigDecimal  | |
| SMALLMONEY | java.math.BigDecimal  | |
| smalldatetime | java.sql.timestamp  | |
| datetime | java.sql.timestamp  | |
| datetime2 | java.sql.timestamp  | |


## <a name="next-steps"></a>Nächste Schritte

+ [Aufrufen von Java in SQL Server](../how-to/call-java-from-sql.md)