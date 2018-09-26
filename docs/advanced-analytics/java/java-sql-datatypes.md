---
title: Java-Datentypen in SQL Server-2019 unterstützt | Microsoft-Dokumentation
description: Zuordnen von Java-Datentypen in SQL Server für Eingabe-und Ausgabedaten Strukturen und für die Eingabeparameter für die Sp_execute_external_script an.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/24/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 3510b53510514daa125382fc10ea33285fe44a80
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2018
ms.locfileid: "46715263"
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