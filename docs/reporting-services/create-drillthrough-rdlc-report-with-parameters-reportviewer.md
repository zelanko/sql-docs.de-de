---
title: Erstellen eines Drillthroughberichts (RDLC) mit Parametern mithilfe von ReportViewer | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über das Erstellen eines Drillthroughberichts (RDLC) mit Parametern und einer Abfrage im Rahmen der Berichtserstellung im lokalen Modus.
ms.date: 05/18/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: 628c8775-c62d-45ac-b349-23db86fa4e6c
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 7f6e6e631b32aa7eab8d6c56c8b6f9e2cf03752f
ms.sourcegitcommit: 783b35f6478006d654491cb52f6edf108acf2482
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91891200"
---
# <a name="create-drillthrough-rdlc-report-with-parameters---reportviewer"></a>Erstellen eines Drillthroughberichts (RDLC) mit Parametern mithilfe von ReportViewer
Ein [Drillthroughbericht](./report-design/drillthrough-reports-report-builder-and-ssrs.md) ist ein Bericht, der geöffnet werden kann, indem der Benutzer auf einen Link in einem anderen Bericht klickt. Drillthroughberichte enthalten in der Regel Details zu einem Element im ursprünglichen Zusammenfassungsbericht. Dieses Tutorial führt Sie in den folgenden Lektionen durch die Schritte zum Erstellen eines Drillthroughberichts mit Parametern und einer Abfrage. Dabei wird die [Berichterstellung im lokalen Modus](report-server-sharepoint/local-mode-vs-connected-mode-reports-in-the-report-viewer.md) verwendet.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
Zur Verwendung dieser exemplarischen Vorgehensweise benötigen Sie Zugriff auf die Beispieldatenbank **AdventureWorks2014** . Weitere Informationen zum Abrufen der **AdventureWorks2014**-Beispieldatenbank finden Sie in den [AdventureWorks-Beispieldatenbanken](https://github.com/Microsoft/sql-server-samples/releases).  
  
Bei dieser exemplarischen Vorgehensweise wird vorausgesetzt, dass Sie mit Transaction-SQL-Abfragen und den ADO.NET-Objekten [DataSet](/dotnet/api/system.data.dataset) und [DataTable](/dotnet/api/system.data.datatable) vertraut sind.  
  
Verwenden Sie Visual Studio 2015 und die ASP.NET-Webanwendung, um eine ASP.NET-Webseite mit einem ReportViewer-Steuerelement zu erstellen. Das Steuerelement wird für die Anzeige eines erstellten Berichts konfiguriert. Mithilfe dieser exemplarischen Vorgehensweise erstellen Sie die Anwendung in Microsoft Visual C#.  
  
## <a name="tasks"></a>Aufgaben  
[Lektion 1: Erstellen einer neuen Website](../reporting-services/lesson-1-create-a-new-web-site.md)  
[Lektion 2: Definieren einer Datenverbindung und einer Datentabelle für den übergeordneten Bericht](../reporting-services/lesson-2-define-a-data-connection-and-data-table-for-parent-report.md)  
[Lektion 3: Entwerfen des übergeordneten Berichts mithilfe des Berichts-Assistenten](../reporting-services/lesson-3-design-the-parent-report-using-the-report-wizard.md)  
[Lektion 4: Definieren einer Datenverbindung und einer Datentabelle für den untergeordneten Bericht](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md)  
[Lesson 5: Entwerfen des untergeordneten Berichts mithilfe des Berichts-Assistenten](../reporting-services/lesson-5-design-the-child-report-using-the-report-wizard.md)  
[Lektion 6: Hinzufügen eines ReportViewer-Steuerelements zur Anwendung](../reporting-services/lesson-6-add-a-reportviewer-control-to-the-application.md)  
[Lektion 7: Hinzufügen einer Drillthroughaktion für den übergeordneten Bericht](../reporting-services/lesson-7-add-drillthrough-action-on-parent-report.md)  
[Lektion 8: Erstellen eines Datenfilters](../reporting-services/lesson-8-create-a-data-filter.md)  
[Lektion 9: Erstellen und Ausführen der Anwendung](../reporting-services/lesson-9-build-and-run-the-application.md)  
  
## <a name="see-also"></a>Weitere Informationen  
[Reporting Services-Tutorials &#40;SSRS&#41;](../reporting-services/reporting-services-tutorials-ssrs.md)  
[Entwerfen von Berichten mithilfe des Berichts-Designers (SSRS)](../reporting-services/tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
