---
title: Erstellen eines Drillthrough-Berichts (RDLC) mit Parametern mithilfe von Report Viewer (SSRS-Tutorial) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 628c8775-c62d-45ac-b349-23db86fa4e6c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7efb713b5dbf9a3f19118bb3572ccd35778aad19
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66109652"
---
# <a name="create-a-drillthrough-rdlc-report-with-parameters-using-reportviewer-ssrs-tutorial"></a>Erstellen eines Drillthroughberichts (RDLC) mit Parametern mithilfe von ReportViewer (SSRS-Lernprogramm)
  Ein [Drillthroughbericht](https://technet.microsoft.com/library/ff519554.aspx) ist ein Bericht, der geöffnet werden kann, indem der Benutzer auf einen Link in einem anderen Bericht klickt. Drillthroughberichte enthalten in der Regel Details zu einem Element im ursprünglichen Zusammenfassungsbericht. Dieses Tutorial führt Sie in den folgenden Lektionen durch die Schritte zum Erstellen eines Drillthroughberichts mit Parametern und einer Abfrage. Dabei wird die [Berichterstellung im lokalen Modus](local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md) verwendet.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 Zur Verwendung dieser exemplarischen Vorgehensweise benötigen Sie Zugriff auf die Beispieldatenbank **AdventureWorks2008** . Die in dieser exemplarischen Vorgehensweise verwendete Abfrage kann auch mit der Datenbank **AdventureWorks2012** verwendet werden. Weitere Informationen dazu, wie Sie auf die Beispieldatenbank **AdventureWorks2008** zugreifen können, finden Sie unter [Anleitung: Installieren der AdventureWorks-Datenbank](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx) für Microsoft Visual Studio 2010.  
  
 Bei dieser exemplarischen Vorgehensweise wird vorausgesetzt, dass Sie mit Transaction-SQL-Abfragen und den ADO.NET-Objekten [DataSet](https://msdn.microsoft.com/library/system.data.dataset\(v=vs.100\).aspx) und [DataTable](https://msdn.microsoft.com/library/system.data.datatable\(v=vs.100\).aspx) vertraut sind.  
  
 Verwenden Sie Visual Studio 2010 oder Visual Studio 2012 und die ASP.NET-Websitevorlage, um eine ASP.NET-Webseite mit einem ReportViewer-Steuerelement zu erstellen. Das Steuerelement wird für die Anzeige eines erstellten Berichts konfiguriert. Mithilfe dieser exemplarischen Vorgehensweise erstellen Sie die Anwendung in Microsoft Visual C#.  
  
## <a name="tasks"></a>Aufgaben  
 [Lektion 1: Erstellen einer neuen Website](../reporting-services/lesson-1-create-a-new-web-site.md)   
 [Lektion 2: Definieren einer Datenverbindung und einer Datentabelle für den übergeordneten Bericht](../reporting-services/lesson-2-define-a-data-connection-and-data-table-for-parent-report.md)   
 [Lektion 3: Entwerfen des übergeordneten Berichts mithilfe des Berichts-Assistenten](../reporting-services/lesson-3-design-the-parent-report-using-the-report-wizard.md)   
 [Lektion 4: Definieren einer Datenverbindung und einer Datentabelle für den untergeordneten Bericht](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md)   
 [Lektion 5: Entwerfen des untergeordneten Berichts mithilfe des Berichts-Assistenten](../reporting-services/lesson-5-design-the-child-report-using-the-report-wizard.md)   
 [Lektion 6: Hinzufügen eines Report Viewer-Steuer Elements zur Anwendung](../reporting-services/lesson-6-add-a-reportviewer-control-to-the-application.md)   
 [Lektion 7: Hinzufügen von Drillthrough-Aktionen für den übergeordneten Bericht](../reporting-services/lesson-7-add-drillthrough-action-on-parent-report.md)   
 [Lektion 8: Erstellen eines Daten Filters](../reporting-services/lesson-8-create-a-data-filter.md)   
 [Lektion 9: Erstellen und Ausführen der Anwendung](../reporting-services/lesson-9-build-and-run-the-application.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Reporting Services Tutorials &#40;SSRS&#41;](../reporting-services/reporting-services-tutorials-ssrs.md)   
 [Entwerfen von Berichten mithilfe des Berichts-Designers (SSRS)](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  
  
