---
title: Sys.external_languages (Transact-SQL) – SQL Server | Microsoft-Dokumentation
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
ms.sourcegitcommit: be09f0f3708f2e8eb9f6f44e632162709b4daff6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2019
ms.locfileid: "65995118"
---
# <a name="sysexternallanguages-transact-sql"></a>sys.external_languages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Diese Katalogsicht enthält eine Liste der externen Sprachen in der Datenbank. **R** und **Python** sind reservierte Namen und mit diesen bestimmten Namen kann keine externe Sprache erstellt werden.

## <a name="sysexternallanguages"></a>sys.external_languages

Der Katalog Ansicht sys.external_languages enthält eine Zeile für jede externe Sprache, in der Datenbank.

|Spaltenname |Datentyp | Description|
|------|------|------|
|external_language_id |ssNoversion | ID der externen Sprache|
|language |sysname |Der Name der externen Sprache. Ist in der Datenbank eindeutig. R und Python sind reservierte Namen pro Instanz|
|create_date |datetime2 |Datum und Uhrzeit der Erstellung|
|principal_id |ssNoversion |ID des Prinzipals, der diese externe Bibliothek besitzt|

## <a name="see-also"></a>Siehe auch  

+ [sys.external_language_files](sys-external-language-files-transact-sql.md)  
+ [ERSTELLEN EXTERNEN SPRACHEN](../../t-sql/statements/create-external-language-transact-sql.md) 
