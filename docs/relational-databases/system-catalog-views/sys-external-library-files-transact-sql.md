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
ms.openlocfilehash: b2f1bbdc3936dc6295b9ecc51b937e50cae20670
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "80664228"
---
# <a name="sysexternal_library_files-transact-sql"></a>sys.external_library_files (Transact-SQL)  
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Listet eine Zeile für jede Datei auf, die eine externe Bibliothek bildet.

|Spaltenname |Datentyp |BESCHREIBUNG|
|------|------|-----|
|external_library_id | INT |ID des externen Bibliotheks Objekts. |
|Inhalt |varbinary(max) |Inhalt des externen Bibliotheksdatei Artefakts. |
|Plattform |TINYINT |ID der Host Plattform, auf der SQL Server installiert ist. |
|platform_desc | nvarchar(60) |Der Name der Host Plattform. Gültige Werte sind "Windows", "Linux". |

### <a name="see-also"></a>Weitere Informationen:  

[sys.external_libraries](sys-external-libraries-transact-sql.md)  
[externe Bibliothek erstellen](../../t-sql/statements/create-external-library-transact-sql.md)  

