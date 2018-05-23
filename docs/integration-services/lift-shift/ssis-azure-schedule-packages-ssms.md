---
title: Planen von SSIS-Paketen in Azure mit SSMS | Microsoft-Dokumentation
description: Beschreibt, wie SSIS-Pakete geplant werden können, die in Azure SQL-Datenbank bereitgestellt werden sollen, indem in SQL Server Management Studio (SSMS) der Befehl „Zeitplan“ verwendet wird.
ms.date: 05/09/2018
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.component: lift-shift
ms.suite: sql
ms.custom: ''
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 72b20d4d42517555449f639cee398db4363d5735
ms.sourcegitcommit: 0cc2cb281e467a13a76174e0d9afbdcf4ccddc29
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2018
---
# <a name="schedule-the-execution-of-an-ssis-package-in-azure-with-sql-server-management-studio-ssms"></a>Planen der Ausführung eines SSIS-Pakets in Azure mit SQL Server Management Studio (SSMS)

SQL Server Management Studio (SSMS) stellt eine Planungsfunktion für SSIS-Pakete bereit, die in Azure SQL-Datenbank bereitgestellt werden. Eine lokale SQL Server-Instanz und eine verwaltete Azure SQL-Datenbank-Instanz (Vorschau) haben den SQL Server-Agent bzw. den Agent für verwaltete Instanzen als erstklassigen SSIS-Auftragsplaner. SQL-Datenbank hat dagegen keinen integrierten erstklassigen SSIS-Auftragsplaner. Das in diesem Artikel beschriebene SSMS-Feature bietet eine vertraute Benutzeroberfläche, die SQL Server-Agent sehr ähnlich ist, zum Planen von Paketen, die in SQL-Datenbank bereitgestellt werden.

Wenn Sie die SSIS-Katalogdatenbank (`SSISDB`) mit SQL-Datenbank hosten, können Sie dieses SSMS-Feature verwenden, um die Data Factory-Pipelines, -Aktivitäten und -Trigger zu generieren, die zum Planen von SSIS-Paketen erforderlich sind. Sie können diese Objekte dann in Data Factory bearbeiten und erweitern.

Wenn Sie mit SSMS ein Paket planen, erstellt SSIS automatisch drei neue Data Factory-Objekte, deren Namen auf dem Namen des ausgewählten Pakets und dem Zeitstempel basieren. Hat das SSIS-Paket beispielsweise den Namen **MeinPaket**, erstellt SSMS neue Data Factory-Objekte, die den folgenden ähneln:

| Objekt | Name |
|---|---|
| Pipeline | **Pipeline_MeinPaket_2018-05-08T09_00_00Z** |
| Ausführen einer SSIS-Paketaktivität | **Activity_MeinPaket_2018-05-08T09_00_00Z** |
| Trigger | **Trigger_MeinPaket_2018-05-08T09_00_00Z** |
|||

## <a name="prerequisites"></a>Voraussetzungen

Das in diesem Artikel beschriebene Feature erfordert SQL Server Management Studio, Version 17.7 oder höher. Die neueste Version von SSMS können Sie unter [Herunterladen von SQL Server Management Studio (SSMS)](../../ssms/download-sql-server-management-studio-ssms.md) abrufen.

## <a name="schedule-a-package-in-ssms"></a>Planen eines Pakets in SSMS

1. Wählen Sie in SSMS im Objekt-Explorer die SSISDB-Datenbank, einen Ordner, ein Projekt und schließlich ein Paket aus. Klicken Sie mit der rechten Maustaste auf das Paket, und wählen Sie **Zeitplan** aus.

    ![Wählen das Paket aus, das geplant werden soll.](media/ssis-azure-schedule-packages-ssms/schedule-ssms-image1-schedule.png)

2. Das Dialogfeld **Neuer Zeitplan** wird geöffnet. Geben Sie im Dialogfeld **Neuer Zeitplan** auf der Seite **Allgemein** den Namen und die Beschreibung für den neuen geplanten Auftrag an.

    ![Seite „Allgemein“ des Dialogfelds „Neuer Zeitplan“](media/ssis-azure-schedule-packages-ssms/schedule-ssms-image2-new-schedule.png)

3. Wählen Sie im Dialogfeld **Neuer Zeitplan** auf der Seite **Paket** die optionalen-Laufzeiteinstellungen und eine Laufzeitumgebung aus.

    ![Seite „Paket“ des Dialogfelds „Neuer Zeitplan“](media/ssis-azure-schedule-packages-ssms/schedule-ssms-image3-new-schedule2.png)

4. Geben Sie im Dialogfeld **Neuer Zeitplan** auf der Seite **Zeitplan** die Zeitplaneinstellungen an, etwa Häufigkeit, Tageszeit und Dauer.

    ![Seite „Zeitplan“ des Dialogfelds „Neuer Zeitplan“](media/ssis-azure-schedule-packages-ssms/schedule-ssms-image4-new-schedule3.png)

5. Nachdem Sie den Auftrag im Dialogfeld **Neuer Zeitplan** erstellt haben, wird eine Bestätigung angezeigt, um Sie an die neuen Data Factory-Objekte zu erinnern, die SSMS erstellen wird. Wenn Sie **Ja** in dem Bestätigungsdialogfeld auswählen, wird die neue Data Factory-Pipeline im Azure-Portal geöffnet, damit Sie sie überprüfen und anpassen können.

    ![Bestätigung des neuen Zeitplans](media/ssis-azure-schedule-packages-ssms/schedule-ssms-image5-confirmation.png)

6. Um den Zeitplantrigger anzupassen, wählen Sie **Neu/Bearbeiten** im Menü **Trigger** aus.

    ![Optionales Bearbeiten der neuen Pipeline](media/ssis-azure-schedule-packages-ssms/schedule-ssms-image6-edit.png)

    Das Blatt **Trigger bearbeiten** wird geöffnet, auf dem Sie die Zeitplanoptionen anpassen können.

    ![Trigger bearbeiten](media/ssis-azure-schedule-packages-ssms/schedule-ssms-image7-edit2.png)

## <a name="next-steps"></a>Nächste Schritte

Informationen über andere Methoden zum Planen eines SSIS-Pakets finden Sie unter [Planen der Ausführung von SSIS-Paketen in Azure](ssis-azure-schedule-packages.md).

Weitere Informationen zu Azure Data Factory-Pipelines, -Aktivitäten und -Triggern finden Sie in den folgenden Artikeln:
-   [Pipelines und Aktivitäten in Azure Data Factory](https://docs.microsoft.com/azure/data-factory/concepts-pipelines-activities)
-   [Pipelineausführung und Trigger in Azure Data Factory](https://docs.microsoft.com/azure/data-factory/concepts-pipeline-execution-triggers)
