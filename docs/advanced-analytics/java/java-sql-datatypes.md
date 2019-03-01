---
title: Java-Datentypen in SQL Server-2019 – SQL Server-Machine Learning-Dienste unterstützt
description: Zuordnen von Java-Datentypen in SQL Server für Eingabe-und Ausgabedaten Strukturen und für die Eingabeparameter für die Sp_execute_external_script an.
ms.prod: sql
ms.technology: machine-learning
ms.date: 02/28/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 4c0f691b8bb389c2da2001d19f0684b7f928f707
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/01/2019
ms.locfileid: "57017816"
---
# <a name="java-and-sql-server-supported-data-types"></a>Java und SQL Server-Datentypen

In diesem Artikel ordnet SQL Server-Datentypen in Java-Datentypen, Datenstrukturen und Parameter für [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

## <a name="data-types-for-data-sets"></a>Datentypen für Datasets

Die folgenden SQL- und Java-Datentypen werden derzeit für Eingabe und Ausgabe-Datasets unterstützt.

| SQL-Datentyp        | Java-Datentyp | Anmerkung | |
| ------------- |-------------|-|
| bit      | boolean | |
| Tinyint      | short      | |
| Smallint | short      | |
| int | ssNoversion      | |
| Real | FLOAT      | |
| Bigint | long      | |
| FLOAT | double      | |
| nchar(n) | Zeichenfolge      | |
| nvarchar(n) | Zeichenfolge  | |
| binary(n) | byte[]      | |
| varbinary(n) | byte[]      | |
| nvarchar(max) | Zeichenfolge | |
| varbinary(max) | byte[] | |
| UNIQUEIDENTIFIER | Zeichenfolge | |
| char(n) | Zeichenfolge | Nur UTF8-Zeichenfolge, die unterstützt |
| varchar (n) | Zeichenfolge | Nur UTF8-Zeichenfolge, die unterstützt |
| varchar(max) | Zeichenfolge | Nur UTF8-Zeichenfolge, die unterstützt |

## <a name="data-types-for-input-parameters"></a>Datentypen für Eingabeparameter

Die folgenden SQL- und Java-Datentypen werden derzeit für Eingabeparameter unterstützt.

| SQL-Datentyp        | Java-Datentyp | Anmerkung | |
| ------------- |-------------|-|-|
| bit      | boolean | | |
| Tinyint      | short      | | |
| Smallint | short      | | |
| int | ssNoversion      | | |
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
| char(n) | Zeichenfolge | Nur UTF8-Zeichenfolge, die unterstützt | |
| varchar (n) | Zeichenfolge | Nur UTF8-Zeichenfolge, die unterstützt | |
| varchar(max) | Zeichenfolge | Nur UTF8-Zeichenfolge, die unterstützt | |

## <a name="see-also"></a>Siehe auch

+ [Gewusst wie: Aufrufen von Java in SQL Server](howto-call-java-from-sql.md)
+ [Java-Beispiel in SQL Server](java-first-sample.md)
+ [Java-spracherweiterung in SQL Server](extension-java.md)