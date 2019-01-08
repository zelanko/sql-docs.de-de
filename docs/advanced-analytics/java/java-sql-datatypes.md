---
title: Java-Datentypen in SQL Server-2019 – SQL Server-Machine Learning-Dienste unterstützt
description: Zuordnen von Java-Datentypen in SQL Server für Eingabe-und Ausgabedaten Strukturen und für die Eingabeparameter für die Sp_execute_external_script an.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/24/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6921a40efc9af3ef94c0a53f8409891fee16127e
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2018
ms.locfileid: "53432533"
---
# <a name="java-and-sql-server-supported-data-types"></a>Java und SQL Server-Datentypen

In diesem Artikel ordnet SQL Server-Datentypen in Java-Datentypen, Datenstrukturen und Parameter für [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

## <a name="data-types-for-data-sets"></a>Datentypen für Datasets

Die folgenden SQL- und Java-Datentypen werden derzeit für Eingabe und Ausgabe-Datasets unterstützt.

| SQL-Typ        | Java-Typ | | |
| ------------- |-------------|-|-|
| bit      | boolean | | |
| Tinyint      | short      | | |
| Smallint | short      | | |
| int | ssNoversion      | | |
| Real | FLOAT      | | |
| Bigint | long      | | |
| FLOAT | double      | | |
| nchar(n) | Zeichenfolge (Unicode)      | | |
| nvarchar (n) | Zeichenfolge (Unicode)      | | |
| binary(n) | byte[]      | | |
| varbinary (n) | byte[]      | | |

## <a name="data-types-for-input-parameters"></a>Datentypen für Eingabeparameter

Die folgenden SQL- und Java-Datentypen werden derzeit für Eingabeparameter unterstützt.

| SQL-Typ        | Java-Typ | | |
| ------------- |-------------|-|-|
| bit      | boolean | | |
| Tinyint      | short      | | |
| Smallint | short      | | |
| int | ssNoversion      | | |
| Real | FLOAT      | | |
| Bigint | long      | | |
| FLOAT | double      | | |
| nchar(n) | Zeichenfolge (Unicode)      | | |
| nvarchar (n) | Zeichenfolge (Unicode)      | | |
| binary(n) | byte[]      | | |
| varbinary (n) | byte[]      | | |
| nvarchar(max) | Zeichenfolge (Unicode)      | | |
| varbinary(max) | byte[]      | | |

## <a name="see-also"></a>Siehe auch

+ [Gewusst wie: Aufrufen von Java in SQL Server](howto-call-java-from-sql.md)
+ [Java-Beispiel in SQL Server](java-first-sample.md)
+ [Java-spracherweiterung in SQL Server](extension-java.md)