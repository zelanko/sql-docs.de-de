---
title: sys. external_libraries (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: machine-learning
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
ms.openlocfilehash: ac6ad0872e813d36d9884a00f979b2a5284cd4a3
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73536158"
---
# <a name="sysexternal_libraries-transact-sql"></a>sys. external_libraries (Transact-SQL)  
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Unterstützt die Verwaltung von Paket Bibliotheken im Zusammenhang mit externen Laufzeiten, wie z. b. R, Python und Java.

> [!NOTE]
> In SQL Server 2017 werden die R-Sprache und die Windows-Plattform unterstützt. R, Python und Java auf den Windows-und Linux-Plattformen werden in SQL Server 2019 und höher unterstützt.

## <a name="sysexternal_libraries"></a>sys.external_libraries

In der Katalog Sicht sys. external_libraries wird eine Zeile für jede externe Bibliothek aufgelistet, die in die Datenbank hochgeladen wurde.

|Spaltenname |Datentyp | Beschreibung|
|------|------|------|
|external_library_id |int | ID des externen Bibliotheks Objekts. |
|name |sysname |Der Name der externen Bibliothek. Ist innerhalb der Datenbank pro Besitzer eindeutig.|
|principal_id |int |ID des Prinzipals, der diese externe Bibliothek besitzt. |
|Sprache | sysname | Der Name der Sprache oder Laufzeit, die die externe Bibliothek unterstützt. Gültige Werte sind ' R ', ' python ' und ' Java '. Weitere Laufzeiten werden möglicherweise in der Zukunft hinzugefügt.|
|Bereich |int |0 für öffentlichen Bereich; 1 für privaten Bereich |  
|scope_desc |varchar (7) |Gibt an, ob das Paket öffentlich oder privat ist.|

## <a name="see-also"></a>Siehe auch  

+ [sys.external_library_files](sys-external-library-files-transact-sql.md)  
+ [externe Bibliothek erstellen](../../t-sql/statements/create-external-library-transact-sql.md)  
+ [Installieren neuer R-Pakete unter SQL Server](../../advanced-analytics/r/install-additional-r-packages-on-sql-server.md)  
+ [Installieren neuer Python-Pakete unter SQL Server](../../advanced-analytics/python/install-additional-python-packages-on-sql-server.md)  