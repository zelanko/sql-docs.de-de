---
title: 'Lektion 1: Erstellen eines Berichtsserverprojekts | Microsoft-Dokumentation'
description: In dieser Lektion erstellen Sie ein Berichtsserverprojekt und eine Berichtsdefinitionsdatei (RDL-Datei) im Berichts-Designer.
ms.date: 12/09/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: 675671ca-e6c9-48a2-82e9-386778f3a49f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: db412b18a0189f9f68caff79f8e904db5424d673
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "75244323"
---
# <a name="lesson-1-create-a-report-server-project-reporting-services"></a>Lektion 1: Erstellen eines Berichtsserverprojekts (Reporting Services)

In dieser Lektion erstellen Sie ein *Berichtsserverprojekt* und eine *Berichtsdefinitionsdatei (RDL-Datei)* im *Berichts-Designer*.

> [!NOTE]
> [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ist eine [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Umgebung zum Erstellen von Business Intelligence-Lösungen. SSDT verfügt über die Erstellungsumgebung des Bericht-Designers, in dem Sie paginierte [!INCLUDE[ssrsnoversion_md](../includes/ssrsnoversion-md.md)] -Berichtsdefinitionen, freigegebene Datenquellen, freigegebene Datasets und Berichtsteile öffnen, ändern, vorher ansehen, speichern und bereitstellen können.

Wenn Sie Berichte mit dem Berichts-Designer erstellen, wird ein Berichtsserverprojekt erstellt, das die Berichtsdateien und andere Ressourcendateien enthält, die von den Berichten verwendet werden.

## <a name="to-create-a-report-server-project"></a>So erstellen Sie ein Berichtsserverprojekt
  
1. Klicken Sie im Menü **Datei** auf **Neu** > **Projekt**.  

    ![ssrs-ssdt-file-01-new-project](../reporting-services/media/ssrs-ssdt-file-01-new-project.png)
  
2. Klicken Sie in der Spalte ganz links unter **Installiert** auf **Reporting Services**. In einigen Fällen ist diese Option unter **Business Intelligence**.

    ![select-report-server-project-template](../reporting-services/media/lesson-1-creating-a-report-server-project-reporting-services/select-report-server-project-template.png)

    > [!IMPORTANT]
    > Wenn in Visual Studio die Option „Reporting Services“ nicht in der linken Spalte angezeigt wird, fügen Sie den Berichts-Designer hinzu, indem Sie die SQL Server Data Tools-Workload installieren. Klicken Sie im Menü **Extras** auf **Tools und Features abrufen...** , und wählen Sie **SQL Server Data Tools** aus den angezeigten Workloads aus. Wenn keine Reporting Services-Objekte in der mittleren Spalte angezeigt werden, fügen Sie die Reporting Services-Erweiterungen hinzu. Wählen Sie aus dem Menü **Extras** **Erweiterungen und Updates** > **Online** aus. Wählen Sie in der mittleren Spalte **Microsoft Reporting Services Projects** > **Download** (Microsoft SQL Server Reporting Services-Projekte > Download) aus den angezeigten Erweiterungen aus. Weitere Informationen zu SQL Server Data Tools finden Sie unter [Herunterladen und Installieren von SQL Server Data Tools (SSDT) für Visual Studio](../ssdt/download-sql-server-data-tools-ssdt.md).

3. Klicken Sie auf das Symbol für das **Berichtsserverprojekt** &nbsp;&nbsp;![ssrs_ssdt_report_server_project](media/ssrs-ssdt-report-server-project.png) &nbsp;&nbsp;in der mittleren Spalte des Dialogfelds **New Project** (Neues Projekt).

4. Geben Sie im Textfeld **Name** „Tutorial“ als Projektnamen ein. Standardmäßig enthält das Textfeld **Speicherort** den Pfad zum Ordner „Dokumente\Visual Studio 20xx\Projects\"“. Der Berichts-Designer erstellt einen Ordner namens „Tutorial“ in diesem Pfad und das Projekt „Tutorial“ in diesem Ordner. Wenn das Projekt nicht zu einer Visual Studio-Projektmappe gehört, erstellt Visual Studio ebenfalls eine Projektmappendatei (SLN-Datei).

5. Klicken Sie auf **OK**, um das Projekt zu erstellen. Das Projekt „Tutorial“ wird rechts im **Projektmappen-Explorer** aufgeführt.
  
## <a name="creating-a-report-definition-file-rdl"></a>Erstellen einer Berichtsdefinitionsdatei (RDL)  
  
1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Berichte**. Wenn der **Projektmappen-Explorer** nicht angezeigt wird, klicken Sie auf **Ansicht** > **Projektmappen-Explorer**.

2. Klicken Sie dann auf **Hinzufügen** > **Neues Element**.

    ![ssrs_ssdt_Bericht_hinzufügen](../reporting-services/media/ssrs-ssdt-add-report.png)

3. Klicken Sie im Fenster **Neues Element hinzufügen** auf das Symbol für **Berichte**.

4. Geben Sie „Sales Orders.rdl“ in das Textfeld **Name** ein.

5. Klicken Sie auf die Schaltfläche zum **Hinzufügen** im unteren rechten Bereich des Dialogfelds **Neues Element hinzufügen**, um den Vorgang abzuschließen. Der Berichts-Designer wird geöffnet, und die Berichtsdatei „Sales Orders.rdl“ wird in der Designansicht angezeigt.

    ![ssrs-ssdt-01-new-report-designer](media/ssrs-ssdt-01-new-report-designer.png)

## <a name="next-steps"></a>Nächste Schritte

Bisher haben Sie das Berichtsprojekt „Tutorial“ und den Bericht „Sales Report“ erstellt. In den verbleibenden Lektionen lernen Sie Folgendes:

- Konfigurieren einer Datenquelle für den Bericht
- Erstellen eines Datasets aus der Datenquelle
- Entwerfen und Formatieren des Berichtslayouts

Fahren Sie fort mit [Lektion 2: Angeben von Verbindungsinformationen &#40;Reporting Services&#41;](../reporting-services/lesson-2-specifying-connection-information-reporting-services.md).
