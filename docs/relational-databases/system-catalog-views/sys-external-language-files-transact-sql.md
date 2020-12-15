---
description: sys.external_language_files (Transact-SQL)-SQL Server
title: sys.external_language_files (Transact-SQL)-SQL Server | Microsoft-Dokumentation
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
monikerRange: '>=sql-server-ver15'
ms.openlocfilehash: f09590931848f963ebe62736d4a890c0cf11ed0d
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97477461"
---
# <a name="sysexternal_language_files-transact-sql"></a>sys.external_language_files (Transact-SQL)
[!INCLUDE[SQL Server 2019](../../includes/applies-to-version/sqlserver2019.md)]

Diese Katalog Sicht enthält eine Liste der externen sprach Erweiterungs Dateien in der Datenbank. **R** und **Python** sind reservierte Namen, und es kann keine externe Sprache mit diesen Namen erstellt werden.

Wenn eine externe Sprache aus einem file_spec erstellt wird, werden die Erweiterung selbst und ihre Eigenschaften in dieser Ansicht aufgeführt. Diese Ansicht enthält einen Eintrag pro Sprache und Betriebssystem.

## <a name="sysexternal_languages"></a>sys.external_languages

In der Katalog Sicht sys.external_language_files wird eine Zeile für jede externe Spracherweiterung in der-Datenbank aufgelistet. Parameter

|Spaltenname |Datentyp | Beschreibung|
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
