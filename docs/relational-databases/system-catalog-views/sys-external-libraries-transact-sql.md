---
title: sys.external_libraries (Transact-SQL) | Microsoft Docs
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
ms.openlocfilehash: 6b1bfc00b403fa76f692db78593ed4c0e6b53ce8
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/04/2020
ms.locfileid: "80664433"
---
# <a name="sysexternal_libraries-transact-sql"></a>sys.external_libraries (Transact-SQL)  
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Unterstützt die Verwaltung von Paketbibliotheken im Zusammenhang mit externen Laufzeiten wie R, Python und Java.

> [!NOTE]
> In SQL Server 2017 werden die R-Sprache und die Windows-Plattform unterstützt. R, Python und Java werden für die Windows- und die Linux-Plattform in SQL Server 2019 und höher unterstützt.

## <a name="sysexternal_libraries"></a>sys.external_libraries

Die Katalogansicht sys.external_libraries listet eine Zeile für jede externe Bibliothek auf, die in die Datenbank hochgeladen wurde.

|Spaltenname |Datentyp | BESCHREIBUNG|
|------|------|------|
|external_library_id |INT | ID des externen Bibliotheksobjekts. |
|name |sysname |Name der externen Bibliothek. Ist innerhalb der Datenbank pro Besitzer eindeutig.|
|principal_id |INT |ID des Prinzipals, dem diese externe Bibliothek gehört. |
|language | sysname | Name der Sprache oder Laufzeit, die die externe Bibliothek unterstützt. Gültige Werte sind 'R', 'Python' und 'Java'. Zusätzliche Laufzeiten können in Zukunft hinzugefügt werden.|
|scope |INT |0 für den öffentlichen Bereich; 1 für den privaten Bereich |  
|scope_desc |varchar(7) |Gibt an, ob das Paket öffentlich oder privat ist|

## <a name="see-also"></a>Siehe auch  

+ [sys.external_library_files](sys-external-library-files-transact-sql.md)  
+ [EXTERNE BIBLIOTHEK ERSTELLEN](../../t-sql/statements/create-external-library-transact-sql.md)  
+ [Installieren neuer R-Pakete unter SQL Server](../../machine-learning/package-management/install-additional-r-packages-on-sql-server.md)  
+ [Installieren neuer Python-Pakete unter SQL Server](../../machine-learning/package-management/install-additional-python-packages-on-sql-server.md)  