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
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 3f6d833488982da777d0f146d55f0a67fa945de5
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2018
ms.locfileid: "39553260"
---
# <a name="sysexternallibraries-transact-sql"></a>Sys.external_libraries (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]


Unterstützt die Verwaltung von im Zusammenhang mit der externen Runtimes wie R oder Python-Paket-Bibliotheken.

## <a name="sysexternallibraries"></a>sys.external_libraries

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
