---
title: sys. external_library_files (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/24/2019
ms.prod: sql
ms.technology: machine-learning
ms.topic: language-reference
f1_keywords:
- external_library_files
- external_library_files_TSQL
- sys.external_library_files
- sys.external_library_files_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.external_library_files catalog view
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d7af0a7fcb639ae3beab6216e77f9b7b95a398da
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68471095"
---
# <a name="sysexternallibraryfiles-transact-sql"></a>sys. external_library_files (Transact-SQL)  
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Listet eine Zeile für jede Datei auf, die eine externe Bibliothek bildet.

|Spaltenname |Datentyp |Beschreibung|
|------|------|-----|
|external_library_id | ssNoversion |ID des externen Bibliotheks Objekts. |
|content |varbinary(max) |Inhalt des externen Bibliotheksdatei Artefakts. |
|Plattform |TINYINT |ID der Host Plattform, auf der SQL Server installiert ist. |
|platform_desc | nvarchar(60) |Der Name der Host Plattform. Gültige Werte sind "Windows", "Linux". |

### <a name="see-also"></a>Siehe auch  

[sys.external_libraries](sys-external-libraries-transact-sql.md)  
[EXTERNE BIBLIOTHEK ERSTELLEN](../../t-sql/statements/create-external-library-transact-sql.md)  
[Paketverwaltung für SQL Server Machine Learning-Dienst](../../advanced-analytics/r/installing-and-managing-r-packages.md)  
