---
title: Sys.external_libraries (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/28/2019
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
ms.openlocfilehash: 3a2f83d703566ae5a60fd027ff7f186205a0c404
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/01/2019
ms.locfileid: "57017536"
---
# <a name="sysexternallibraries-transact-sql"></a>sys.external_libraries (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Unterstützt die Verwaltung von paketbibliotheken, die im Zusammenhang mit der externen Runtimes wie R, Python und Java.

> [!NOTE]
> In SQL Server 2017 werden R-Sprache und Windows-Plattform unterstützt. R, Python und Java auf der Windows-Plattform werden in 2019 CTP 2.3 von SQL Server unterstützt. Unterstützung für Linux ist für ein späteres Release geplant.

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