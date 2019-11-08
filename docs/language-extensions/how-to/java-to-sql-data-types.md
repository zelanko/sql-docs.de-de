---
title: In SQL Server 2019 unterstützte Java-Datentypen
titleSuffix: SQL Server Language Extensions
description: Ordnen Sie Java-Datentypen für Ein- und Ausgabedatenstrukturen und für Eingabeparameter für „sp_execute_external_script“ SQL Server zu.
author: dphansen
ms.author: davidph
ms.date: 09/05/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 9daca9c607befe077fcccec20385a36c82b04c6f
ms.sourcegitcommit: a97d551b252b76a33606348082068ebd6f2c4c8c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2019
ms.locfileid: "73588834"
---
# <a name="java-and-sql-server-supported-data-types"></a>Von Java und SQL Server unterstützte Datentypen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Artikel werden SQL Server-Datentypen für Datenstrukturen und Parameter für [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) Java-Datentypen zugeordnet.

Die folgenden SQL- und Java-Datentypen werden derzeit für Eingabe-/Ausgabedatasets und Eingabe-/Ausgabeparameter unterstützt.

| SQL-Datentyp        | Java-Datentyp | Anmerkung | |
| ------------- |-------------|-|-|
| bit      | boolean | | |
| Tinyint      | short      | | |
| Smallint | short      | | |
| int | INT      | | |
| Real | FLOAT      | | |
| Bigint | long      | | |
| FLOAT | double      | | |
| nchar(n) | Zeichenfolge      | | |
| nvarchar(n) | Zeichenfolge      | | |
| binary(n) | byte[]      | | |
| varbinary(n) | byte[]      | | |
| nvarchar(max) | Zeichenfolge      | | |
| varbinary(max) | byte[]      | | |
| UNIQUEIDENTIFIER | Zeichenfolge | | |
| char(n) | Zeichenfolge | Nur UTF8-Zeichenfolgen werden unterstützt. | |
| varchar(n) | Zeichenfolge | Nur UTF8-Zeichenfolgen werden unterstützt. | |
| varchar(max) | Zeichenfolge | Nur UTF8-Zeichenfolgen werden unterstützt. | |
| date | java.sql.date  | | |
| NUMERIC | java.math.BigDecimal  | | |
| Decimal | java.math.BigDecimal  | | |
| money | java.math.BigDecimal  | | |
| SMALLMONEY | java.math.BigDecimal  | | |
| smalldatetime | java.sql.timestamp  | | |
| DATETIME | java.sql.timestamp  | | |
| datetime2 | java.sql.timestamp  | | |


## <a name="next-steps"></a>Nächste Schritte

+ [Aufrufen von Java in SQL Server](../how-to/call-java-from-sql.md)
