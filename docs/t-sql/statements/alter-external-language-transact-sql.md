---
description: ALTER EXTERNAL LANGUAGE (Transact-SQL) – SQL Server
title: ALTER EXTERNAL LANGUAGE (Transact-SQL) – SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.technology: language-extensions
ms.topic: language-reference
author: nelgson
ms.author: negust
ms.reviewer: dphansen
manager: cgronlun
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a102301cfa1e168fff01473176e8b6787ade06dc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88479127"
---
# <a name="alter-external-language-transact-sql"></a>ALTER EXTERNAL LANGUAGE (Transact-SQL)
[!INCLUDE [SQL Server 2019 and later](../../includes/applies-to-version/sqlserver2019.md)]

Ändert den Inhalt einer vorhandenen externen Spracherweiterung in der Datenbank.

## <a name="syntax"></a>Syntax

```text
ALTER EXTERNAL LANGUAGE language_name  
[ AUTHORIZATION owner_name ]
{
    SET <file_spec>
    | ADD <file_spec>
    | REMOVE <file_spec>
}
[ ; ]  

<file_spec> ::=  
{
    ( CONTENT = {<external_lang_specifier> | <content_bits>,
    FILE_NAME = <external_lang_file_name>
    [, PLATFORM = <platform> ]
    [, PARAMETERS = <external_lang_parameters> ]
    [, ENVIRONMENT_VARIABLES = <external_lang_env_variables> ] )
}

<external_lang_specifier> :: =  
{
    '[file_path\]os_file_name'  
}

<content_bits> :: =  
{
    varbinary_literal
   | varbinary_expression
}

<external_lang_file_name> :: =  
'extension_file_name'

<platform> :: =
{
   WINDOWS
  | LINUX
}

< external_lang_parameters > :: =  
'extension_specific_parameters'
```

### <a name="arguments"></a>Argumente

**language_name**

Sprachen sind datenbankweite Objekte. Sprachnamen müssen innerhalb der Datenbank eindeutig sein.

**owner_name**

Gibt den Namen eines Benutzers oder einer Rolle an, der oder die die externe Sprache besitzt. Wird kein Wert angegeben, wird der aktuelle Benutzer zum Besitzer. Je nach Berechtigungen muss anderen Benutzern möglicherweise die explizite Berechtigung zum Ausführen von Skripts unter Verwendung einer bestimmten Sprache erteilt werden.

**file_spec**

Gibt den Inhalt der Spracherweiterung an. Es ist nur eine Dateiangabe für eine bestimmte Sprache pro Plattform zulässig. 

**external_lang_specifier**

Der vollständige Dateipfad zur ZIP- oder TAR.GZ-Datei mit dem Erweiterungscode. Dieser Inhalt kann entweder ein Pfad zu einer ZIP-Datei (unter Windows) oder einer TAR.GZ-Datei (unter Linux) sein.

**content_bits**

Gibt ähnlich wie bei Assemblys den Inhalt der Sprache als Hexadezimalliteral an.
Diese Option ist hilfreich, wenn Sie eine Sprache erstellen oder eine bestehende Sprache ändern müssen (und über die erforderlichen Berechtigungen dafür verfügen), das Dateisystem auf dem Server jedoch eingeschränkt ist und Sie die Bibliotheksdateien nicht an einen Speicherort kopieren können, auf den der Server Zugriff hat.

**external_lang_file_name**

Der Name der DLL- oder SO-Datei der Erweiterung. Dieser ist erforderlich, um die richtige Datei in solchen Fällen zu identifizieren, in denen mehrere DLL- oder SO-Dateien in der ZIP- oder TAR.GZ-Datei für <external_lang_specifier> vorhanden sind.

**external_lang_parameters**

Dies bietet eine Möglichkeit, einen Satz von Parametern für die Runtime der externen Sprache bereitzustellen. Parameterwerte werden der Runtime der externen Sprache nach dem Starten des externen Prozesses bereitgestellt. Auf Umgebungsvariablen kann die Spracherweiterung jedoch vor dem Starten des externen Prozesses zugreifen.

**external_lang_env_variables**

Dies bietet eine Möglichkeit, einen Satz von Umgebungsvariablen für die Runtime der externen Sprache vor dem Starten des externen Prozesses bereitzustellen. Ein Beispiel für eine Umgebungsvariable ist das Basisverzeichnis der Runtime selbst. Beispiel: JRE_HOME.

**platform**

Dieser Parameter ist für Szenarien mit hybridem Betriebssystem erforderlich. In einer hybriden Architektur muss die Sprache einmal pro Plattform registriert werden. Plattform und Sprachname sind der eindeutige Schlüssel für jede externe Sprache. Wenn keine Plattform angegeben ist, wird vom aktuellen Betriebssystem davon ausgegangen.

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="remarks"></a>Bemerkungen

Derzeit werden **PARAMETERS** und **ENVIRONMENT_VARIABLES** nicht unterstützt.

## <a name="permissions"></a>Berechtigungen

Erfordert die `ALTER ANY EXTERNAL LANGUAGE`-Berechtigung. Standardmäßig verfügt jeder Benutzer mit **dbo**, der Mitglied der Rolle **db_owner** ist, über die Berechtigung zum Ändern einer externen Sprache. Allen anderen Benutzern müssen Sie die Berechtigung mithilfe einer [GRANT](https://docs.microsoft.com/sql/t-sql/statements/grant-database-permissions-transact-sql)-Anweisung explizit gewähren, in der Sie ALTER ANY EXTERNAL LANGUAGE als Berechtigung angeben.

## <a name="examples"></a>Beispiele

### <a name="alter-an-external-language-in-a-database"></a>Ändern einer externen Sprache in einer Datenbank  

Im folgenden Beispiel wird eine externe Sprache mit dem Namen Java einer Datenbank auf SQL Server unter Windows hinzugefügt.

```sql
ALTER EXTERNAL LANGUAGE Java 
SET (CONTENT = N'<path-to-zip>', FILE_NAME = 'javaextension.dll');
GO
```

## <a name="see-also"></a>Weitere Informationen

[CREATE EXTERNAL LANGUAGE (Transact-SQL)](create-external-language-transact-sql.md)  
[DROP EXTERNAL LANGUAGE (Transact-SQL)](drop-external-language-transact-sql.md)  
[sys.external_languages](../../relational-databases/system-catalog-views/sys-external-languages-transact-sql.md)  
[sys.external_language_files](../../relational-databases/system-catalog-views/sys-external-language-files-transact-sql.md)  
