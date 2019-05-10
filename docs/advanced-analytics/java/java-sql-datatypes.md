---
title: Java-Datentypen in SQL Server-2019 - Spracherweiterungen für SQL Server unterstützt
description: Zuordnen von Java-Datentypen in SQL Server für Eingabe-und Ausgabedaten Strukturen und für die Eingabeparameter für die Sp_execute_external_script an.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/23/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 14a2bc5594b16610dfb8278ab82a9e7b8b22fea6
ms.sourcegitcommit: d5cd4a5271df96804e9b1a27e440fb6fbfac1220
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2019
ms.locfileid: "64775003"
---
# <a name="java-and-sql-server-supported-data-types"></a>Java und SQL Server-Datentypen

In diesem Artikel ordnet SQL Server-Datentypen in Java-Datentypen, Datenstrukturen und Parameter für [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

## <a name="data-types-for-data-sets"></a>Datentypen für Datasets

Die folgenden SQL- und Java-Datentypen werden derzeit für Eingabe und Ausgabe-Datasets unterstützt.


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

## <a name="next-steps"></a>Nächste Schritte

+ [Gewusst wie: Aufrufen von Java in SQL Server](howto-call-java-from-sql.md)
+ [Java-Beispiel in SQL Server](java-first-sample.md)
+ [Java-spracherweiterung in SQL Server](extension-java.md)
