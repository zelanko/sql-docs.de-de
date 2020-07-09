---
title: Notebooks mit Python-Kernel in Azure Data Studio
description: In diesem Tutorial erfahren Sie, wie Sie ein Python-Notebook erstellen und ausführen.
author: garyericson
ms.author: garye
ms.reviewer: mikeray, alayu, maghan
ms.topic: tutorial
ms.prod: azure-data-studio
ms.technology: ''
ms.custom: ''
ms.date: 04/27/2020
ms.openlocfilehash: e4c431cba395b8e0c732fa7ac4ab96942cac7144
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85728862"
---
# <a name="create-and-run-a-python-notebook"></a>Erstellen und Ausführen eines Python-Notebooks

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

In diesem Tutorial wird veranschaulicht, wie Sie mithilfe des Python-Kernels ein Notebook in Azure Data Studio erstellen und ausführen.

## <a name="prerequisites"></a>Voraussetzungen

- [Installierte Azure Data Studio-Instanz](download-azure-data-studio.md)

## <a name="new-notebook"></a>Neues Notebook

Führen Sie die folgenden Schritte aus, um eine Notebook-Datei in Azure Data Studio zu erstellen:

1. Öffnen Sie Azure Data Studio. Wenn Sie dazu aufgefordert werden, eine Verbindung mit einer SQL Server-Instanz herzustellen, können Sie diese Verbindung herstellen oder auf **Abbrechen** klicken.

1. Klicken Sie im Menü **Datei** auf **Neues Notebook**.

1. Wählen Sie **Python 3** als **Kernel** aus.

   :::image type="content" source="media/notebook-tutorial-python/set-kernel-and-attach-to-python.png" alt-text="Festlegen des Kernels":::

1. Wenn Sie dazu aufgefordert werden, Python zu konfigurieren, wählen Sie unter **Python für Notebooks konfigurieren** eine der folgenden Optionen aus:

   - **Neue Python-Installation**, um eine neue Kopie von Python für Azure Data Studio zu installieren, oder
   - **Vorhandene Python-Installation verwenden**, um den Pfad zu einer vorhandenen Python-Installation anzugeben

## <a name="run-a-notebook-cell"></a>Ausführen einer Notebookzelle

Sie können Zellen erstellen, die Code oder Text enthalten. Sie können eine Codezelle direkt ausführen. Die Ergebnisse werden im Notebook angezeigt, sobald die Ausführung der Zelle abgeschlossen ist. Mit Textzellen können Sie Ihren Code mit formatierter Dokumentation versehen.

### <a name="code"></a>Code

Fügen Sie eine neue Python-Codezelle hinzu, indem Sie in der Symbolleiste auf den Befehl **+ Code** klicken.

:::image type="content" source="media/notebook-tutorial-python/notebook-toolbar-python.png" alt-text="Notebook-Symbolleiste":::

In diesem Beispiel wird eine einfache Berechnung durchgeführt.

```python
a = 1
b = 2
c = a/b
print(c)
```
Führen Sie die Zelle aus, indem Sie links neben der Zelle auf die Wiedergabeschaltfläche klicken. Die Ergebnisse werden unten angezeigt.

:::image type="content" source="media/notebook-tutorial-python/run-notebook-cell-python.png" alt-text="Ausführen der Notebook-Zelle":::

### <a name="text"></a>Text

Klicken Sie auf der Symbolleiste auf den Befehl **+ Text**, um eine neue Textzelle hinzuzufügen.

:::image type="content" source="media/notebook-tutorial-python/notebook-toolbar-python-text.png" alt-text="Notebook-Symbolleiste":::

Die Zelle wechselt in den Bearbeitungsmodus. Geben Sie nun Markdown-Text ein, und Ihnen wird gleichzeitig die Vorschauversion angezeigt.

:::image type="content" source="media/notebook-tutorial-python/notebook-markdown-cell-python.png" alt-text="Markdown-Zelle":::

Wenn Sie außerhalb der Textzelle klicken, wird nur der Markdown-Text angezeigt.

:::image type="content" source="media/notebook-tutorial-python/notebook-markdown-preview-python.png" alt-text="Markdown-Text":::

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie mehr über Notebooks:

- [Verwenden von Notebooks in SQL Server](notebooks-guidance.md)

- [Erstellen und Ausführen eines SQL Server-Notebooks](notebooks-tutorial-sql-kernel.md)

- [How to manage notebooks in Azure Data Studio (Vorgehensweise: Verwalten von Notebooks in Azure Data Studio)](notebooks-manage-sql-server.md)
