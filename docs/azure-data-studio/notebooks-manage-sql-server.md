---
title: Verwalten eines Notebooks
description: Erfahren Sie, wie Sie Notebooks in Azure Data Studio verwalten. Hierzu gehört das Öffnen und Speichern von Notebooks sowie das Ändern der SQL-Verbindung und des Python-Kernels.
author: markingmyname
ms.author: maghan
ms.reviewer: achatter, alayu, mikeray
ms.metadata: seo-lt-2019
ms.topic: conceptual
ms.prod: azure-data-studio
ms.technology: ''
ms.custom: ''
ms.date: 04/27/2020
ms.openlocfilehash: 326e0b0afc4809d13cf2fdfdbd76f53dafe1cbb9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85774580"
---
# <a name="how-to-manage-notebooks-in-azure-data-studio"></a>Verwalten von Notebooks in Azure Data Studio

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

In diesem Artikel erfahren Sie, wie Sie Notebookdateien in Azure Data Studio öffnen und speichern. Sie erfahren außerdem, wie Sie die Verbindung mit Ihrer SQL Server-Instanz oder Ihrem Python-Kernel ändern.

## <a name="open-a-notebook"></a>Öffnen eines Notebooks

Es gibt verschiedene Möglichkeiten, das Dialogfeld **Notebook öffnen** anzuzeigen. Die können das Menü „Datei“, das Dashboard und die Befehlspalette verwenden. Diese Methoden werden in den nächsten Abschnitten beschrieben.

### <a name="file-menu"></a>Menü „Datei“

Wählen Sie im Menü „Datei“ die Option **Datei öffnen** aus (STRG+O unter Windows und BEFEHLSTASTE+O unter Mac).

![Anzeigen des Dialogfelds „Datei öffnen“ durch Auswählen von „Datei öffnen“](./media/notebooks-manage-sql-server/open-file-1.png)

### <a name="dashboard"></a>Dashboard

Klicken Sie auf dem Dashboard auf **Notebook öffnen**, um das Dialogfeld „Datei öffnen“ anzuzeigen.

![Anzeigen des Dialogfelds „Datei öffnen“ durch Auswählen von „Notebook öffnen“ auf dem Dashboard](./media/notebooks-manage-sql-server/open-file-2.png) 

### <a name="command-palette"></a>Befehlspalette

Verwenden Sie den Befehl **File: Open** aus der Befehlspalette, indem Sie STRG+UMSCHALT+P (unter Windows) oder BEFEHLSTASTE+P (unter Mac) drücken.

![Öffnen des Dialogfelds „Datei öffnen“ durch Eingabe von „File:Open“ in der Befehlspalette](./media/notebooks-manage-sql-server/open-file-3.png)

## <a name="save-a-notebook"></a>Speichern eines Notebooks

Zurzeit gibt es nur eine Möglichkeit, ein Notebook zu speichern. Klicken Sie dazu in der Symbolleiste des Notebooks auf **Speichern**.

![Speichern einer Datei durch Klicken auf „Speichern“ in der Symbolleiste des Notebooks](./media/notebooks-manage-sql-server/save-file-1.png)

> [!NOTE]
> Mit den folgenden Methoden werden Änderungen an Notebooks derzeit nicht gespeichert:
>
> - Befehle **Datei speichern**, **Datei speichern unter...** und **Alle Dateien speichern** im Menü „Datei“.
> - **File: Save**-Befehle, die in der Befehlspalette eingegeben werden.

## <a name="change-the-sql-connection"></a>Ändern der SQL-Verbindung

Gehen Sie zum Ändern der SQL-Verbindung für ein Notebook folgendermaßen vor:

1. Klicken Sie in der Symbolleiste des Notebooks auf das Menü **Anfügen an**, und wählen Sie anschließend die Option **Verbindung ändern** aus.

   ![Klicken auf das Menü „Anfügen an“ in der Symbolleiste des Notebooks](./media/notebooks-manage-sql-server/select-attach-to-1.png)

2. Hier können Sie entweder einen zuletzt verwendeten Verbindungsserver auswählen oder neue Verbindungsdetails für die Verbindung eingeben.

   ![Auswählen eines Servers im Menü „Anfügen an“](./media/notebooks-manage-sql-server/select-attach-to-2.png)

## <a name="change-the-python-kernel"></a>Ändern des Python-Kernels

Wenn Sie Azure Data Studio zum ersten Mal öffnen, wird die Seite **Python für Notebooks konfigurieren** angezeigt. Sie können eine der folgenden Optionen auswählen:

- **Neue Python-Installation**, um eine neue Kopie von Python für Azure Data Studio zu installieren, oder
- **Vorhandene Python-Installation verwenden**, um den Pfad zu einer vorhandenen Python-Installation anzugeben, die Azure Data Studio verwenden soll

Erstellen Sie eine Codezelle, und führen Sie die folgenden Python-Befehle aus, um den Speicherort und die Version des aktiven Python-Kernels anzuzeigen:

```python
import os
import sys
print(sys.version_info)
print(os.path.dirname(sys.executable))
```

So wechseln Sie zu einer anderen Python-Installation:

1. Klicken Sie im Menü **Datei** auf **Einstellungen** und anschließend auf **Einstellungen**.
1. Scrollen Sie unter **Erweiterungen** zu **Notebook-Konfiguration**.
1. Deaktivieren Sie unter **Verwenden vorhandener Python-Installation** die Option „Lokaler Pfad zu einer bereits vorhandenen Python-Installation, die von Notebooks verwendet wird“.
1. Starten Sie Azure Data Studio neu.

Wenn die Seite **Python für Notebooks konfigurieren** angezeigt wird, können Sie auswählen, ob Sie eine neue Python-Installation erstellen oder einen Pfad zu einer vorhandenen Installation angeben möchten.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu SQL-Notebooks in Azure Data Studio finden Sie unter [Notebooks mit SQL Server in Azure Data Studio](notebooks-guidance.md).
