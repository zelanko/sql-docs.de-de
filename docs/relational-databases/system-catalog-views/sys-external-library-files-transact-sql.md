---
title: sys.external_library_files (Transact-SQL) | Microsoft Docs
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
ms.openlocfilehash: b2f1bbdc3936dc6295b9ecc51b937e50cae20670
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/04/2020
ms.locfileid: "80664228"
---
# <a name="sysexternal_library_files-transact-sql"></a>sys.external_library_files (Transact-SQL)  
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Listet eine Zeile für jede Datei auf, aus der eine externe Bibliothek hervortritt.

|Spaltenname |Datentyp |BESCHREIBUNG|
|------|------|-----|
|external_library_id | INT |ID des externen Bibliotheksobjekts. |
|Inhalt |varbinary(max) |Inhalt des externen Bibliotheksdateiartefakts. |
|platform |TINYINT |ID der Hostplattform, auf der SQL Server installiert ist. |
|platform_desc | nvarchar(60) |Name der Hostplattform. Gültige Werte sind 'WINDOWS', 'LINUX'. |

### <a name="see-also"></a>Siehe auch  

[sys.external_libraries](sys-external-libraries-transact-sql.md)  
[EXTERNE BIBLIOTHEK ERSTELLEN](../../t-sql/statements/create-external-library-transact-sql.md)  

