---
title: sys. external_languages (Transact-SQL)-SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.reviewer: dphansen
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- external_languages
- external_languages_TSQL
- sys.external_languages
- sys.external_languages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.external_languages catalog view
author: nelgson
ms.author: negust
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 1cef52f066a07032240d17f88297b02ba3f7e5fb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "65995118"
---
# <a name="sysexternal_languages-transact-sql"></a>sys. external_languages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Diese Katalog Sicht enthält eine Liste der externen Sprachen in der Datenbank. **R** und **python** sind reservierte Namen, und es kann keine externe Sprache mit diesen spezifischen Namen erstellt werden.

## <a name="sysexternal_languages"></a>sys.external_languages

In der Katalog Sicht sys. external_languages wird eine Zeile für jede externe Sprache in der Datenbank aufgelistet.

|Spaltenname |Datentyp | BESCHREIBUNG|
|------|------|------|
|external_language_id |INT | ID der externen Sprache|
|language |sysname |Der Name der externen Sprache. Ist in der Datenbank eindeutig. R und python sind reservierte Namen pro Instanz.|
|create_date |datetime2 |Datum und Uhrzeit der Erstellung|
|principal_id |INT |ID des Prinzipals, der diese externe Bibliothek besitzt.|

## <a name="see-also"></a>Weitere Informationen  

+ [sys.external_language_files](sys-external-language-files-transact-sql.md)  
+ [externe Sprache erstellen](../../t-sql/statements/create-external-language-transact-sql.md) 
