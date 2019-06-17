---
title: Sys.external_libraries (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/27/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- external_libraries
- external_libraries_TSQL
- sys.external_libraries
- sys.external_libraries_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.external_libraries catalog view
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d56d0c69b9e3bae87dda9b55d241a1c040210ca9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62637469"
---
# <a name="sysexternallibraries-transact-sql"></a>sys.external_libraries (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Unterstützt die Verwaltung von paketbibliotheken, die im Zusammenhang mit der externen Runtimes wie R, Python und Java.

> [!NOTE]
> In SQL Server 2017 werden die R-Sprache und die Windows-Plattform unterstützt. R, Python und Java werden für die Windows- und die Linux-Plattform in SQL Server 2019 CTP 2.4 unterstützt.

## <a name="sysexternallibraries"></a>sys.external_libraries

Der Katalog Ansicht sys.external_libraries enthält eine Zeile für jede externe Bibliothek, die in die Datenbank hochgeladen wurde.

|Spaltenname |Datentyp | Description|
|------|------|------|
|external_library_id |ssNoversion | Die ID des Objekts, externe Bibliothek. |
|NAME |sysname |Der Name der externen Bibliothek. Ist eindeutig innerhalb der Datenbank und Besitzer.|
|principal_id |ssNoversion |Die ID des Prinzipals, der diese externe Bibliothek besitzt. |
|language | sysname | Der Name der Sprache oder Runtime, die die externe Bibliothek unterstützt. Gültige Werte sind "R", "Python" und "Java". Zusätzliche Laufzeiten können in Zukunft hinzugefügt werden.|
|Bereich |ssNoversion |0 für Öffentliche Bereich; 1 für privaten Bereich |  
|scope_desc |vom Datentyp varchar(7) |Gibt an, ob das Paket öffentlich oder privat ist.|

## <a name="see-also"></a>Siehe auch  

+ [sys.external_library_files](sys-external-library-files-transact-sql.md)  
+ [CREATE EXTERNAL LIBRARY](../../t-sql/statements/create-external-library-transact-sql.md)  
+ [Installieren neuer R-Pakete unter SQL Server](../../advanced-analytics/r/install-additional-r-packages-on-sql-server.md)  
+ [Installieren neuer Python-Pakete unter SQL Server](../../advanced-analytics/python/install-additional-python-packages-on-sql-server.md)  