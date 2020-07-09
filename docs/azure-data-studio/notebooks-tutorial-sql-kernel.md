---
title: Erstellen eines Notebooks mit dem SQL-Kernel in Azure Data Studio
description: In diesem Tutorial erfahren Sie, wie Sie ein SQL Server-Notebook erstellen und ausführen.
author: markingmyname
ms.author: maghan
ms.reviewer: mikeray, alayu
ms.topic: tutorial
ms.prod: azure-data-studio
ms.technology: ''
ms.custom: ''
ms.date: 03/30/2020
ms.openlocfilehash: 64e5bcfa188707e784d33a6504b120c4ce0ea553
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85735323"
---
# <a name="create-and-run-a-sql-server-notebook"></a>Erstellen und Ausführen eines SQL Server-Notebooks

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

In diesem Tutorial wird veranschaulicht, wie Sie mithilfe von SQL Server ein Notebook in Azure Data Studio erstellen und ausführen.

## <a name="prerequisites"></a>Voraussetzungen

- [Installierte Azure Data Studio-Instanz](download-azure-data-studio.md)
- Installierte SQL Server-Instanz
  - [Windows](../database-engine/install-windows/install-sql-server.md)
  - [Linux](../linux/sql-server-linux-setup.md)

## <a name="new-notebook"></a>Neues Notebook

Führen Sie die folgenden Schritte aus, um eine Notebook-Datei in Azure Data Studio zu erstellen:

1. Stellen Sie in Azure Data Studio eine Verbindung mit Ihrer SQL Server-Instanz her.

2. Wählen Sie unter **Verbindungen** im Fenster **Server** Ihre SQL Server-Instanz aus. Klicken Sie anschließend auf **Neues Notebook**.

   ![Notebook öffnen](media/notebook-tutorial/azure-data-studio-open-notebook.png)

3. Warten Sie, bis die Felder für den **Kernel** und den Zielkontext (**Anfügen an**) ausgefüllt sind. Vergewissern Sie sich, dass der **Kernel** auf **SQL** festgelegt ist. Legen Sie im Feld **Anfügen an** Ihre SQL Server-Instanz (in diesem Fall *localhost*) fest.

   ![„Kernel“ und „Anfügen an“ festlegen](media/notebook-tutorial/set-kernel-and-attach-to.png)

## <a name="run-a-notebook-cell"></a>Ausführen einer Notebookzelle

Sie können jede Notebookzelle ausführen, indem Sie auf das Symbol für Ausführen klicken, das sich links neben der Zelle befindet. Die Ergebnisse werden im Notebook angezeigt, nachdem das Ausführen der Zelle abgeschlossen ist.

### <a name="code"></a>Code

Klicken Sie auf der Symbolleiste auf den Befehl **+ Code**, um eine neue Codezelle hinzuzufügen.

![Notebook-Symbolleiste](media/notebooks-guidance/notebook-toolbar.png)

Im folgenden Beispiel wird eine neue Datenbank erstellt:

```sql
USE master
GO

   -- Drop the database if it already exists
IF  EXISTS (
        SELECT name
        FROM sys.databases
        WHERE name = N'TestNotebookDB'
   )
DROP DATABASE TestNotebookDB
GO

-- Create the database
CREATE DATABASE TestNotebookDB
GO
```

   ![Notebookzelle ausführen](media/notebook-tutorial/run-notebook-cell.png)

Wenn Sie ein Skript ausführen, das ein Ergebnis zurückgibt, können Sie dieses Ergebnis in folgenden Formaten speichern:

- Als CSV speichern
- Als Excel speichern
- Als JSON speichern
- Als XML speichern

In diesem Fall wird das Ergebnis von [PI](../t-sql/functions/pi-transact-sql.md) zurückgegeben.

```sql
SELECT PI() AS PI;
GO
```

![Notebookzelle ausführen](media/notebook-tutorial/run-notebook-cell-2.png)

### <a name="text"></a>Text

Klicken Sie auf der Symbolleiste auf den Befehl **+ Text**, um eine neue Textzelle hinzuzufügen.

![Notebook-Symbolleiste](media/notebooks-guidance/notebook-toolbar.png)

Die Zelle wechselt in den Bearbeitungsmodus. Geben Sie nun „Markdown“ ein, und Ihnen wird gleichzeitig die Vorschauversion angezeigt.

![Markdown-Zelle](media/notebooks-guidance/notebook-markdown-cell.png)

Wenn Sie außerhalb der Textzelle klicken, wird der Markdowntext angezeigt.

![Markdown-Text](media/notebooks-guidance/notebook-markdown-preview.png)

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie mehr über Notebooks:

- [Verwenden von Notebooks in SQL Server](notebooks-guidance.md)

- [How to manage notebooks in Azure Data Studio (Vorgehensweise: Verwalten von Notebooks in Azure Data Studio)](notebooks-manage-sql-server.md)

- [Ausführen eines Beispielnotebooks mithilfe von Spark](../big-data-cluster/notebooks-tutorial-spark.md)