---
title: Erstellen von wieder verwendbaren Codeausschnitten
titleSuffix: Azure Data Studio
description: Informationen Sie zum Erstellen und Verwenden von SQL-Codeausschnitte in Azure Data Studio
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 627608797eb287f9fcf36d8a00df3da1fc8eff75
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66803838"
---
# <a name="create-and-use-code-snippets-to-quickly-create-transact-sql-t-sql-scripts-in-includename-sosincludesname-sos-shortmd"></a>Erstellen und Verwenden von Codeausschnitten in Transact-SQL (T-SQL)-Skripts schnell erstellen [!INCLUDE[name-sos](../includes/name-sos-short.md)]

Codeausschnitte in [!INCLUDE[name-sos](../includes/name-sos-short.md)] sind Vorlagen, die Ihnen erleichtern zu erstellen, Datenbanken und Datenbankobjekte. 

[!INCLUDE[name-sos](../includes/name-sos-short.md)] enthält mehrere T-SQL-Codeausschnitte, um Unterstützung bei der Generierung schnell der richtigen Syntax. 

Eine benutzerdefinierte Codeausschnitte können auch erstellt werden.

## <a name="using-built-in-t-sql-code-snippets"></a>Verwenden von integrierten T-SQL-Codeausschnitten

1. Geben Sie den Zugriff auf die verfügbaren Codeausschnitte *Sql* im Abfrage-Editor, um die Liste zu öffnen:

   ![Ausschnitte](media/code-snippets/sql-snippets.png)

1. Wählen Sie den Ausschnitt, die, den Sie verwenden möchten, und das T-SQL-Skript generiert. Wählen Sie z. B. *SqlCreateTable*:

   ![Tabelle-Ausschnitte erstellen](media/code-snippets/create-table.png)

1. Aktualisieren Sie die hervorgehobenen Feldern durch Ihre eigenen Werte. Ersetzen Sie z. B. *TableName* und *Schema* mit den Werten für Ihre Datenbank:

   ![Ersetzen Sie die Vorlagenfeld](media/code-snippets/table-from-snippet.png)

   Wenn das Feld, das Sie ändern möchten, nicht mehr hervorgehoben ist (Dies geschieht, wenn Sie den Cursor im Editor zu verschieben), mit der rechten Maustaste in des Worts, das Sie verwenden möchten, ändern, und wählen Sie **ändern Sie alle Vorkommnisse**:

   ![Ersetzen Sie die Vorlagenfeld](media/code-snippets/change-all.png)

1. Aktualisieren Sie, oder fügen Sie alle zusätzlichen T-SQL Sie für den ausgewählten Ausschnitt müssen hinzu. Aktualisieren Sie z. B. *Column1*, *Column2*, und fügen Sie weitere Spalten hinzu.


 
## <a name="creating-sql-code-snippets"></a>Erstellen von SQL-Codeausschnitten 

Sie können Ihre eigenen Ausschnitte definieren. Um die SQL-Codeausschnitt-Datei zur Bearbeitung zu öffnen:

1. Öffnen der *Befehlspalette* (**UMSCHALT + STRG + P**), und geben *Snip*, und wählen Sie **Einstellungen: Öffnen Sie User Snippets**:

   ![Ersetzen Sie die Vorlagenfeld](media/code-snippets/user-snippets.png)

1. Wählen Sie **SQL**:

   > [!NOTE]
   > [!INCLUDE[name-sos](../includes/name-sos-short.md)] erbt die Codeausschnitt-Funktionalität von Visual Studio Code, damit in diesem Artikel speziell erläutert die Verwendung von SQL-Ausschnitten. Weitere Informationen finden Sie unter [eigene Ausschnitte erstellen](https://code.visualstudio.com/docs/editor/userdefinedsnippets) in der Dokumentation zu Visual Studio Code. 

   ![Ersetzen Sie die Vorlagenfeld](media/code-snippets/select-sql.png)

1. Fügen Sie den folgenden Code in *sql.json*:

   ```sql
   {
   "Select top 5": {
    "prefix": "sqlSelectTop5",
    "body": "SELECT TOP 5 * FROM ${1:TableName}",
    "description": "User-defined snippet example 1"
    },
    "Create Table snippet":{
    "prefix": "sqlCreateTable2",
    "body": [
    "-- Create a new table called '${1:TableName}' in schema '${2:SchemaName}'",
    "-- Drop the table if it already exists",
    "IF OBJECT_ID('$2.$1', 'U') IS NOT NULL",
    "DROP TABLE $2.$1",
    "GO",
    "-- Create the table in the specified schema",
    "CREATE TABLE $2.$1",
    "(",
    "   $1Id INT NOT NULL PRIMARY KEY, -- primary key column",
    "   Column1 [NVARCHAR](50) NOT NULL,",
    "   Column2 [NVARCHAR](50) NOT NULL",
    "   -- specify more columns here",
    ");",
    "GO"
    ],
   "description": "User-defined snippet example 2"
   }
   }
   ```

1. Speichern Sie die sql.json-Datei.
1. Öffnen Sie ein neues Abfrage-Editor-Fenster, indem Sie auf **STRG + N**.
2. Typ **Sql**, und Sie sehen, dass die beiden Codeausschnitte, die Sie gerade hinzugefügt haben, *sqlCreateTable2* und *sqlSelectTop5*.

Wählen Sie eine neue Ausschnitte aus, und geben sie einen Testlauf aus!


## <a name="additional-resources"></a>Weitere Ressourcen

Weitere Informationen zu den SQL-Editor, finden Sie unter [Code-Editor-Tutorials](tutorial-sql-editor.md).
