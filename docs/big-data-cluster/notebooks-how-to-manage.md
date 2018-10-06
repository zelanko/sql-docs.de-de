---
title: 'Gewusst wie: Verwalten von Notebooks in Azure Data Studio | Microsoft-Dokumentation'
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: ca756c81dcf54f42cb46be4b0f412ce9630814af
ms.sourcegitcommit: 4832ae7557a142f361fbf0a4e2d85945dbf8fff6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2018
ms.locfileid: "48796744"
---
# <a name="how-to-manage-notebooks-in-azure-data-studio"></a>Gewusst wie: Verwalten von Notebooks in Azure Data Studio

In diesem Artikel wird das Öffnen und speichern Notebook-Dateien in Azure Data Studio mit der Vorschau von SQL Server-2019 veranschaulicht. Es veranschaulicht auch so ändern Sie die Verbindung in Ihrer SQL Server-big Data-Cluster.

## <a name="prerequisites"></a>Vorraussetzungen

In diesem Artikel wird davon ausgegangen, dass Sie bereits ein Notebook, das Sie in Azure Data Studio verwenden möchten. Wenn Sie ein Notebook zu erstellen möchten, finden Sie unter [Verwendung von Notebooks in der Vorschau von SQL Server-2019](notebooks-guidance.md). Um Notebooks in Azure Data Studio verwenden zu können, müssen die folgenden Voraussetzungen erfüllt sein:

- [Installieren Sie die neuesten big Data-Tools für die Vorschau von SQL Server-2019](deploy-big-data-tools.md).
- [Bereitstellen einen big Data-Cluster](quickstart-big-data-cluster-deploy.md).

## <a name="open-a-notebook"></a>Öffnen Sie ein notebook

Es gibt mehrere Möglichkeiten zum Öffnen der **Notebook öffnen** Dialogfeld. Sie können das Menü "Datei", das Dashboard und die Befehlspalette verwenden. Den folgenden Abschnitten werden die einzelnen Methoden.

### <a name="file-menu"></a>Menü "Datei"

Wählen Sie **Datei öffnen** aus dem Menü "Datei" STRG + O (in Windows) und Cmd + e/A (im Mac).

![Öffnen Sie das Dialogfeld "Datei öffnen", indem Sie die Datei öffnen auswählen](./media/notebooks-how-to-manage/open-file-1.png) 

### <a name="dashboard"></a>Dashboard

Klicken Sie auf **Notebook öffnen** im Dashboard, um das Dialogfeld "Datei öffnen" zu öffnen.

![Öffnen Sie das Dialogfeld "Datei öffnen", indem Sie Sie im Dashboard Notizbuch öffnen auswählen](./media/notebooks-how-to-manage/open-file-2.png) 

### <a name="command-palette"></a>Befehlspalette

Verwenden Sie Befehl **Datei: Open** über die befehlspalette, indem Sie STRG + UMSCHALT + P (in Windows) und Cmd + UMSCHALT + P (in Mac) eingeben.

![Öffnen Sie das Dialogfeld "Datei öffnen", indem Sie Sie in der befehlspalette File:Open eingeben](./media/notebooks-how-to-manage/open-file-3.png)

## <a name="save-a-notebook"></a>Speichern eines Notebooks

Zurzeit besteht eine Möglichkeit zum Speichern eines Notebooks. Sie müssen auswählen, **speichern** aus der Notebook-Symbolleiste.

![Speichern Sie die Datei durch Klicken auf Speichern der Notebook-Symbolleiste](./media/notebooks-how-to-manage/save-file-1.png)

> [!NOTE]
> Die folgenden Methoden werden derzeit nicht Notebooks speichern:
>
> - **Datei speichern**, **Datei speichern unter...**  und **Datei Alles speichern** Befehle über das Menü Datei.
> - **Datei: Speichern Sie** Befehle in der befehlspalette den Befehl eingegeben wurden.

## <a name="change-the-big-data-cluster"></a>Ändern Sie die big Data-cluster

So ändern Sie die SQL Server-big Data-Cluster für ein Notebook:

1. Klicken Sie auf die **Anfügen an** im Menü auf der Symbolleiste Notebook.

   ![Klicken Sie auf die an den in der Notebook-Symbolleiste im anhängen](./media/notebooks-how-to-manage/select-attach-to-1.png)

2. Klicken Sie auf einen Server aus der **Anfügen an** Menü.

   ![Wählen Sie einen Server aus der Anfügevorgang zum Menü "](./media/notebooks-how-to-manage/select-attach-to-2.png)

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Notebooks in Azure Data Studio, finden Sie unter [Verwendung von Notebooks in der Vorschau von SQL Server-2019](notebooks-guidance.md).