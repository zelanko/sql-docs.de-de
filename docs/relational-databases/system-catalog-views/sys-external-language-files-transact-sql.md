---
title: Sys.external_language_files (Transact-SQL) – SQL Server | Microsoft-Dokumentation
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
ms.openlocfilehash: 0d1325311ef0b708f5a3abd5f4494e099863efc2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65995088"
---
# <a name="sysexternallanguagefiles-transact-sql"></a>sys.external_language_files (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Diese Katalogsicht enthält eine Liste der Erweiterungsdateien externer Sprachen in der Datenbank. **R** und **Python** sind reservierte Namen, und es kann keine externe Sprache mit diesen Namen erstellt werden.

Wenn eine externe Sprache, die aus einer File_spec erstellt wird, werden die Erweiterung selbst und seine Eigenschaften in dieser Ansicht aufgeführt. Diese Sicht enthält einen Eintrag pro Sprache, die pro Betriebssystem.

## <a name="sysexternallanguages"></a>sys.external_languages

Der Katalog Ansicht sys.external_language_files enthält eine Zeile für jede externe Language-Erweiterung in der Datenbank. Parameter

|Spaltenname |Datentyp | Beschreibung|
|------|------|------|
|external_language_id |ssNoversion | ID der externen Sprache|
|content|varbinary(max) |Inhalt der Erweiterungsdatei externer Sprachen|
|file_name|nvarchar(266)|Name der Datei, Sprache-Erweiterung|
|Plattform|TINYINT|ID der die Hostplattform, auf der SQL Server installiert ist|
|platform_desc |nvarchar(60)|Der Name der Hostplattform. Gültige Werte sind "WINDOWS", "LINUX".|
|Parameter|nvarchar(4000)|Externe Language prameters|
|environment_variables |nvarchar(4000)|Externe Language-Umgebungsvariablen|

## <a name="see-also"></a>Siehe auch  

+ [sys.external_languages](sys-external-languages-transact-sql.md)  
+ [ERSTELLEN EXTERNEN SPRACHEN](../../t-sql/statements/create-external-language-transact-sql.md)  
