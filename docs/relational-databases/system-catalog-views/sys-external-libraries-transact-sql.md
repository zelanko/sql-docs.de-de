---
title: Sys.external_libraries (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/05/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
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
author: jeannt
ms.author: jeannt
manager: craigg
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 110f514c4688536decfd29c412ce310746cd972e
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38001192"
---
# <a name="sysexternallibraries-transact-sql"></a>Sys.external_libraries (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]


Unterstützt die Verwaltung von im Zusammenhang mit der externen Runtimes wie R oder Python-Paket-Bibliotheken.

## <a name="sysexternallibraries"></a>Sys.external_libraries

Der Katalog Ansicht sys.external_libraries enthält eine Zeile für jede externe Bibliothek, die in die Datenbank hochgeladen wurde.

|Spaltenname |Datentyp | Description|
|------|------|------|
|external_library_id |ssNoversion | Die ID des Objekts, externe Bibliothek. |
|NAME |sysname |Der Name der externen Bibliothek. Ist eindeutig innerhalb der Datenbank und Besitzer.|
|principal_id |ssNoversion |Die ID des Prinzipals, der diese externe Bibliothek besitzt. |
|Sprache | sysname | Der Name der Sprache oder Runtime, die die externe Bibliothek unterstützt. Gültige Werte sind 'R'. Zusätzliche Laufzeiten können in Zukunft hinzugefügt werden.|
|Bereich |ssNoversion |0 für Öffentliche Bereich; 1 für privaten Bereich |  
|scope_desc |vom Datentyp varchar(7) |Gibt an, ob das Paket öffentlich oder privat ist.|


## <a name="see-also"></a>Siehe auch  
[sys.external_library_files](sys-external-library-files-transact-sql.md)  
[CREATE EXTERNAL LIBRARY](../../t-sql/statements/create-external-library-transact-sql.md)  
[Paketverwaltung für SQL Server R Services](../../advanced-analytics/r/installing-and-managing-r-packages.md)  
