---
title: Verwalten eines SQL Server-Notebooks
description: Erfahren Sie, wie Sie Notebooks in Azure Data Studio verwalten. Hierzu gehört das Öffnen und Speichern von Notebooks sowie das Ändern der Verbindung mit Ihrem Big Data-Cluster.
author: markingmyname
ms.author: maghan
ms.reviewer: achatter, alayu, mikeray
ms.metadata: seo-lt-2019
ms.topic: conceptual
ms.prod: sql
ms.technology: azure-data-studio
ms.custom: ''
ms.date: 03/30/2020
ms.openlocfilehash: 9b071a9d1b9e770e1443e5df539208baa4399a30
ms.sourcegitcommit: 1124b91a3b1a3d30424ae0fec04cfaa4b1f361b6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/01/2020
ms.locfileid: "80531593"
---
# <a name="how-to-manage-notebooks-in-azure-data-studio"></a>Verwalten von Notebooks in Azure Data Studio

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel erfahren Sie, wie Sie Notebookdateien in Azure Data Studio mit SQL Server öffnen und speichern. Sie erfahren außerdem, wie Sie die Verbindung zu Ihrer SQL Server-Instanz ändern.

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

## <a name="change-the-connection"></a>Ändern der Verbindung

Gehen Sie zum Ändern der Verbindung für ein Notebook folgendermaßen vor:

1. Klicken Sie in der Symbolleiste des Notebooks auf das Menü **Anfügen an**, und wählen Sie anschließend die Option **Verbindung ändern** aus.

   ![Klicken auf das Menü „Anfügen an“ in der Symbolleiste des Notebooks](./media/notebooks-manage-sql-server/select-attach-to-1.png)

2. Hier können Sie entweder einen zuletzt verwendeten Verbindungsserver auswählen oder neue Verbindungsdetails für die Verbindung eingeben.

   ![Auswählen eines Servers im Menü „Anfügen an“](./media/notebooks-manage-sql-server/select-attach-to-2.png)

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Notebooks in Azure Data Studio finden Sie unter [Verwenden von Notebooks in SQL Server 2019](notebooks-guidance.md).
