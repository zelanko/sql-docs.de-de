---
title: Verbinden eines Filters oder Dokumentewebparts (Reporting Services im integrierten SharePoint-Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Filter Web Part [Reporting Services]
- SharePoint integration [Reporting Services], Web Parts
- Report Viewer Web Part [Reporting Services]
- Documents Web Part [Reporting Services]
ms.assetid: 6a303135-c0ef-44cd-a423-1cea8df3dcf3
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 7f4722a2b338b0187bdd93cb9501e626c42acf02
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48166890"
---
# <a name="connect-filter-or-documents-web-part-reporting-services-in-sharepoint-integrated-mode"></a>Verbinden eines Filters oder Dokumentwebparts (Reporting Services im integrierten SharePoint-Modus)
  Wenn Sie ein SharePoint-Produkt verwenden, können Sie ein Dashboard oder eine Webpartseite erstellen, die ein Filterwebpart oder ein Dokumentewebpart und ein Berichts-Viewer-Webpart enthält. Unterstützte Versionen sind [!INCLUDE[SPF2010](../includes/spf2010-md.md)] oder [!INCLUDE[SPS2010](../includes/sps2010-md.md)]. Ebenfalls unterstützt wird [!INCLUDE[winSPServ3](../includes/winspserv3-md.md)] oder [!INCLUDE[offSPServ](../includes/offspserv-md.md)] 2007. Durch Verbinden eines Filterwebparts können Benutzer, die Filterwerte in einem Filterwebpart auswählen, den Wert an einen parametrisierten Bericht auf derselben Seite senden. Durch Verbinden eines Dokumentewebparts können Benutzer, die auf Berichte in der Bibliothek Dokumente klicken, den Bericht in einem zugehörigen Berichts-Viewer-Webpart anzeigen.  
  
 Das Filterwebpart wird zum Senden von Werten an mindestens einen Parameter in einem Bericht verwendet. Wenn Sie ein Filterwebpart verwenden möchten, müssen für den Bericht Parameter definiert sein, die mit den vom Webpart gesendeten Werten, Datentypen und dem Format kompatibel sind.  
  
 Das Dokumentewebpart ist der Bibliothek Dokumente der Website Home zugeordnet. Klicken Sie auf **Alle Websiteinhalte einblenden**, um Elemente aus der Bibliothek Dokumente anzuzeigen, hinzuzufügen oder zu entfernen. Klicken Sie in Bibliotheken auf **Dokumente**. Mit den Menüs **Neu**, **Upload**und **Aktionen** können Sie die Elemente in der Bibliothek Dokumente verwalten.  
  
### <a name="to-connect-a-filter-web-part"></a>So verbinden Sie ein Filterwebpart  
  
1.  Öffnen oder erstellen Sie eine Webpartseite oder ein Dashboard.  
  
2.  Klicken Sie im Menü **Websiteaktionen** auf **Seite bearbeiten**.  
  
3.  Klicken Sie auf **Webpart hinzufügen**.  
  
4.  Wählen Sie unter **Alle Webparts**in der Kategorie **Verschiedenes** die Option **Berichts-Viewer für SQL Reporting Services**aus.  
  
5.  Klicken Sie auf **Hinzufügen**. Der Webpart wird oben in der Zone hinzugefügt.  
  
6.  Klicken Sie in einer anderen Zone auf derselben Webpartseite oder demselben Dashboard auf **Webpart hinzufügen**.  
  
7.  Wählen Sie unter **Alle Webparts**im Abschnitt **Filter** ein Webpart aus.  
  
8.  Klicken Sie auf **Hinzufügen**. Der Webpart wird oben in der Zone hinzugefügt.  
  
9. Klicken Sie in der Zone mit dem Webpart auf das Menü **bearbeiten** des Webparts, zeigen Sie auf **Verbindungen**, zeigen Sie auf **Filterwerte senden an**, und wählen Sie anschließend **Berichts-Viewer** - *Berichtsname*.  
  
10. Checken Sie Ihre Änderungen ein, und speichern Sie die Seite.  
  
### <a name="to-connect-a-documents-web-part"></a>So verbinden Sie ein Dokumentwebpart  
  
1.  Öffnen oder erstellen Sie eine Webpartseite oder ein Dashboard.  
  
2.  Klicken Sie im Menü **Websiteaktionen** auf **Seite bearbeiten**.  
  
3.  Klicken Sie auf **Webpart hinzufügen**.  
  
4.  Wählen Sie unter **Alle Webparts**im Abschnitt **Listen und Bibliotheken** die Option **Dokumente**aus.  
  
5.  Klicken Sie auf **Hinzufügen**. Der Webpart wird oben in der Zone hinzugefügt.  
  
6.  Klicken Sie unten im Toolbereich auf **Anwenden** , und klicken Sie anschließend auf **OK** , um den Bereich zu schließen.  
  
7.  Klicken Sie in einer anderen Zone auf derselben Webpartseite oder demselben Dashboard auf **Webpart hinzufügen**.  
  
8.  Wählen Sie unter **Alle Webparts**in der Kategorie **Verschiedenes** die Option **Berichts-Viewer für SQL Reporting Services.**  
  
9. Klicken Sie auf **Hinzufügen**. Der Webpart wird oben in der Zone hinzugefügt.  
  
10. Klicken Sie in der Zone mit dem Webpart auf das Menü **bearbeiten** des Webparts, zeigen Sie auf **Verbindungen**, zeigen Sie auf **Berichtsdefinitionen abrufen von**, und wählen Sie anschließend **Dokumente**aus.  
  
11. Checken Sie Ihre Änderungen ein, und speichern Sie die Seite.  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen des Berichts-Viewer-Webparts zu einer Webseite &#40;integrierten Reporting Services im SharePoint-Modus&#41;](report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md)   
 [Berichts-Viewer-Webpart auf einer SharePoint-Website](../../2014/reporting-services/report-viewer-web-part-on-a-sharepoint-site.md)   
 [Customize the Report Viewer Web Part (Anpassen des Berichts-Viewer-Webparts)](../../2014/reporting-services/customize-the-report-viewer-web-part.md)  
  
  
