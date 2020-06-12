---
title: sys. external_language_files (Transact-SQL)-SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
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
ms.reviewer: dphansen
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a991761e26f8f63ae6431d7d242fb2625135d3ac
ms.sourcegitcommit: 1be90e93980a8e92275b5cc072b12b9e68a3bb9a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84627477"
---
# <a name="sysexternal_language_files-transact-sql"></a>sys. external_language_files (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Diese Katalog Sicht enthält eine Liste der externen sprach Erweiterungs Dateien in der Datenbank. **R** und **Python** sind reservierte Namen, und es kann keine externe Sprache mit diesen Namen erstellt werden.

Wenn eine externe Sprache aus einem file_spec erstellt wird, werden die Erweiterung selbst und ihre Eigenschaften in dieser Ansicht aufgeführt. Diese Ansicht enthält einen Eintrag pro Sprache und Betriebssystem.

## <a name="sysexternal_languages"></a>sys.external_languages

In der Katalog Sicht sys. external_language_files wird eine Zeile für jede externe Spracherweiterung in der-Datenbank aufgelistet. Parameter

|Spaltenname |Datentyp | BESCHREIBUNG|
|------|------|------|
|external_language_id |INT | ID der externen Sprache|
|Inhalt|varbinary(max) |Inhalt der externen sprach Erweiterungs Datei|
|file_name|nvarchar (266)|Name der sprach Erweiterungs Datei|
|platform|TINYINT|ID der Host Plattform, auf der SQL Server installiert ist|
|platform_desc |nvarchar(60)|Der Name der Host Plattform. Gültige Werte sind "Windows", "Linux".|
|parameters|nvarchar(4000)|Externe Sprachen-Prameter|
|environment_variables |nvarchar(4000)|Umgebungsvariablen für externe Sprache|

## <a name="see-also"></a>Weitere Informationen  

+ [sys.external_languages](sys-external-languages-transact-sql.md)  
+ [externe Sprache erstellen](../../t-sql/statements/create-external-language-transact-sql.md)  
