---
title: Sys.external_library_files (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/05/2017
ms.prod: sql
ms.technology: system-objects
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
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a9666b58132feb79876c4e8074dc530440c05b2c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47828058"
---
# <a name="sysexternallibraryfiles-transact-sql"></a>Sys.external_library_files (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Enthält eine Zeile für jede Datei, die aus einer externen Bibliothek besteht.

|Spaltenname |Datentyp |Description|
|------|------|-----|
|external_library_id | ssNoversion |Die ID des Objekts, externe Bibliothek. |
|content |varbinary(max) |Der Inhalt des Artefakts Datei externe Bibliothek. |
|Plattform |TINYINT |ID der die Hostplattform, auf der SQL Server installiert ist. |
|platform_desc | nvarchar(60) |Der Name der Hostplattform. Gültige Werte sind "WINDOWS", "LINUX". |

### <a name="see-also"></a>Siehe auch  

[sys.external_libraries](sys-external-libraries-transact-sql.md)  
[CREATE EXTERNAL LIBRARY](../../t-sql/statements/create-external-library-transact-sql.md)  
[Paketverwaltung für SQL Server Machine Learning-Dienst](../../advanced-analytics/r/installing-and-managing-r-packages.md)  
