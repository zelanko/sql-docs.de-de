---
title: Berichts-Viewer-Webpart-Programmierbarkeit in SharePoint-Integration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 714017b7-1bd6-4950-a3c6-d0df8450a877
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 43c0988abc3ea5043873421054fc370a58ed9347
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36147632"
---
# <a name="report-viewer-web-part-programmability-in-sharepoint-integration"></a>Berichts-Viewer-Webpart-Programmierbarkeit in SharePoint-Integration
  Der Berichts-Viewer-Webpart ist ein `T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart`-Serversteuerelement, das einen Satz von öffentlichen Anwendungsprogrammierschnittstellen (API) enthält, der Entwicklern ermöglicht, benutzerdefinierte SharePoint-Anwendungen zu erstellen. Sie können benutzerdefinierte Webparts erstellen, die Berichtspfad und Parameter mit Webpartverbindungen zu Berichts-Viewer-Webparts angeben. Sie können auch das Webpart in eine benutzerdefinierte SharePoint-Webpartseite einbetten und es mit der öffentlichen API anpassen.  
  
## <a name="connecting-to-report-viewer-web-part-with-custom-web-parts"></a>Herstellen einer Verbindung mit Berichts-Viewer-Webpart mit benutzerdefinierten Webparts  
 Der Berichts-Viewer-Webpart ist ein Verbindungsconsumer zu SharePoint-Webparts, die <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> oder `T:Microsoft.SharePoint.WebPartPages.IFilterValues` implementieren. Ein <xref:System.Web.UI.WebControls.WebParts.IWebPartRow>-Webpart wie das **Dokumente**-Webpart kann einen Berichtspfad zu einem Berichts-Viewer-Webpart angeben, wenn es auf der gleichen Webpartseite wie das Berichts-Viewer-Webpart platziert wird. Ebenso ein `T:Microsoft.SharePoint.WebPartPages.IFilterValues` -Webpart, z. B. die **Textfilter** oder die **Auswahlfilter**, geben Sie einen Berichtsparameter mit einem Berichts-Viewer-Webpart auf derselben Seite wie den Berichts-Viewer-Webpart platziert können Teil.  
  
### <a name="implementing-a-report-path-provider-with-iwebpartrow"></a>Implementieren eines Berichtspfadanbieters mit IWebPartRow  
 Um durch Webpartverbindungen einen Berichtspfad zum Berichts-Viewer-Webpart anzugeben, gehen Sie wie folgt vor:  
  
1.  Erstellen Sie einen Webpart, der die <xref:System.Web.UI.WebControls.WebParts.IWebPartRow>-Schnittstelle implementiert.  
  
2.  Fügen Sie den Webpart zur selben Webpartseite wie den Berichts-Viewer-Webpart hinzu.  
  
3.  Verbinden Sie den Webpart mit dem Berichts-Viewer-Webpart in der webbasierten Webpart-Entwurfsbenutzeroberfläche.  
  
    > [!NOTE]  
    >  Sie können nur jeweils ein <xref:System.Web.UI.WebControls.WebParts.IWebPartRow>-Webpart mit dem Berichts-Viewer-Webpart verbinden, und Sie können nicht ein <xref:System.Web.UI.WebControls.WebParts.IWebPartRow>-Webpart und ein `T:Microsoft.SharePoint.WebPartPages.IFilterValues`-Webpart mit dem Berichts-Viewer-Webpart verbinden.  
  
 Damit der <xref:System.Web.UI.WebControls.WebParts.IWebPartRow>-Webpart ordnungsgemäß mit dem `T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart`-Webpart funktioniert, müssen Sie Folgendes in der <xref:System.Web.UI.WebControls.WebParts.IWebPartRow.GetRowData%2A>-Methode durchführen:  
  
-   Rufen Sie die Rückrufmethode mit einem <xref:System.Data.DataRowView>-Objekt als Eingabeparameter auf.  
  
-   Stellen Sie sicher, dass das <xref:System.Data.DataRowView>-Objekt eine Spalte mit dem Namen "DocUrl" enthält, die den Berichtspfad enthält.  
  
    > [!NOTE]  
    >  Das Berichts-Viewer-Webpart im Add-In für [!INCLUDE[offSPServ](../includes/offspserv-md.md)] 2010 unterstützt auch das Empfangen von Berichtspfaden, die die Spalte "FileRef" verwenden.  
  
### <a name="implementing-a-report-parameter-provider-with-ifiltervalues"></a>Implementieren eines Berichtsparameteranbieters mit IFilterValues  
 Ein Webpart, der `T:Microsoft.SharePoint.WebPartPages.IFilterValues` implementiert, kann einen Parameterwert für den Berichts-Viewer-Webpart bereitstellen. Der an den Berichts-Viewer-Webpart gesendete Parameterwert unterliegt gemäß der Angabe in der Berichtsdefinition denselben Einschränkungen wie der Berichtsparameter, zum Beispiel Datentyp, gültige Werte usw.  
  
 Um dem Berichts-Viewer-Webpart einen Berichtsparameter bereitzustellen, gehen Sie wie folgt vor:  
  
1.  Erstellen Sie einen Webpart, der die `T:Microsoft.SharePoint.WebPartPages.IFilterValues`-Schnittstelle implementiert.  
  
2.  Fügen Sie den Webpart zur selben Seite wie den `T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart`-Webpart hinzu.  
  
3.  Verbinden Sie den `T:Microsoft.SharePoint.WebPartPages.IFilterValues`-Webpart mit dem Berichts-Viewer-Webpart in der webbasierten Webpart-Entwurfsbenutzeroberfläche.  
  
    > [!NOTE]  
    >  Sie können mehrere `T:Microsoft.SharePoint.WebPartPages.IFilterValues`-Webparts gleichzeitig mit dem Berichts-Viewer-Webpart verbinden. Sie können jedoch nicht sowohl ein <xref:System.Web.UI.WebControls.WebParts.IWebPartRow>-Webpart als auch ein `T:Microsoft.SharePoint.WebPartPages.IFilterValues`-Webpart gleichzeitig mit dem Berichts-Viewer-Webpart verbinden.  
  
## <a name="see-also"></a>Siehe auch  
 [IFilterValues-Schnittstelle](https://msdn.microsoft.com/en-us/library/office/microsoft.sharepoint.webpartpages.ifiltervalues\(v=office.15\).aspx)  
  
  