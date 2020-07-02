---
title: sys. external_library_files (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/25/2020
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
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=azuresqldb-mi-current||=sqlallproducts-allversions'
ms.openlocfilehash: 69c1b1c0f1ec2c7ab1c6cd17fbf949f0aaf166f2
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85754486"
---
# <a name="sysexternal_library_files-transact-sql"></a>sys.external_library_files (Transact-SQL)  
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

Listet eine Zeile für jede Datei auf, die eine externe Bibliothek bildet.

|Spaltenname |Datentyp |BESCHREIBUNG|
|------|------|-----|
|external_library_id | INT |ID des externen Bibliotheks Objekts. |
|Inhalt |varbinary(max) |Inhalt des externen Bibliotheksdatei Artefakts. |
|platform |TINYINT |ID der Host Plattform, auf der SQL Server installiert ist. |
|platform_desc | nvarchar(60) |Der Name der Host Plattform. Gültige Werte sind "Windows", "Linux". |

### <a name="see-also"></a>Weitere Informationen  

[sys.external_libraries](sys-external-libraries-transact-sql.md)  
[externe Bibliothek erstellen](../../t-sql/statements/create-external-library-transact-sql.md)  
