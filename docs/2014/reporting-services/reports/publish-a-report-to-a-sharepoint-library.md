---
title: Veröffentlichen eines Berichts in einer SharePoint-Bibliothek | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deploying [Reporting Services], reports in SharePoint integrated mode
- SharePoint integration [Reporting Services], publishing to a library
- publishing reports [Reporting Services], to a SharePoint library
ms.assetid: 3f6dfc28-50d8-4231-bd25-871b5f77cce6
caps.latest.revision: 14
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: d19618eaa7997444e661ca9213a72f75bf1b3910
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058233"
---
# <a name="publish-a-report-to-a-sharepoint-library"></a>Veröffentlichen eines Berichts in einer SharePoint-Bibliothek
  Wenn Sie einen Bericht auf einer für die SharePoint-Integration konfigurierten SharePoint-Website veröffentlichen möchten, müssen Sie die Berichtsprojekteigenschaften im Berichts-Designer festlegen. In den Projekteigenschaften müssen alle Verweise auf Server, Berichte und freigegebene Datenquellen vollqualifizierte URLs sein. Zudem muss es sich in einer Berichtsdefinition bei allen Verweisen auf eingebettete Berichte, Drillthroughberichten und Ressourcen (z. B. webbasierte Bilder) um vollqualifizierte URLs handeln.  
  
 Sie müssen für die SharePoint-Website über die Berechtigung als **Mitglied** oder **Besitzer** verfügen, um die Eigenschaften für das Projekt festzulegen. Weitere Informationen finden Sie unter [Beispiele für URLs von veröffentlichten Berichtselementen auf einem Berichtsserver im SharePoint-Modus &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md).  
  
### <a name="to-publish-a-report-to-a-sharepoint-site"></a>So veröffentlichen Sie einen Bericht auf einer SharePoint-Website  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]öffnen Sie ein vorhandenes oder neues Berichtsserverprojekt.  
  
2.  Klicken Sie im Menü **Projekt** auf **Eigenschaften**. Das Dialogfeld *\<Projekt>***Eigenschaftenseiten** wird geöffnet.  
  
3.  Wählen Sie in der Liste **Konfiguration** den Namen einer Projektmappenkonfiguration aus, die Sie zum Erstellen und Veröffentlichen Ihres Berichts verwenden können. Die aktuelle Konfiguration wird als **Active**(*\<Konfiguration>*) (Aktiv) aufgelistet.  
  
4.  Wenn Sie die freigegebenen Datenquellen in Ihrem Projekt veröffentlichen und bereits veröffentlichte freigegebene Datenquellen überschreiben möchten, legen Sie **OverwriteDataSources** auf **True**fest.  
  
5.  (Optional) Für **TargetDataSourceFolder**, geben Sie eine URL zu einer SharePoint-Bibliothek oder einem Bibliotheksordner (z. B. *http://TestServer/TestSite/Documents/DataSources)*.  
  
     Wenn Sie keinen Wert angeben, wird der Wert **TargetReportFolder** verwendet.  
  
6.  Für **TargetReportFolder**, geben Sie eine URL zu einer Bibliothek oder einem Bibliotheksordner (z. B. *http://TestServer/TestSite/Documents/Reports)*.  
  
7.  Geben Sie für **TargetServerURL**eine URL zu einer SharePoint-Website auf oberster Ebene oder zu einer Unterwebsite ein. Wenn Sie keine Website angeben, wird die standardmäßige Stammwebsite verwendet (z. B. *http://servername*, *http://servername/site*, oder *http://servername/site/subsite*).  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
9. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Bericht, den Sie veröffentlichen möchten, und klicken Sie auf **Bereitstellen**. Der Bericht wird an dem in **TargetReportFolder**angegebenen Speicherort veröffentlicht. Im Ausgabefenster werden Bereitstellungsfehler angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaftsseiten für Projekt (Dialogfeld)](../tools/project-property-pages-dialog-box.md)   
 [Festlegen von Bereitstellungseigenschaften &#40;Reporting Services&#41;](../tools/set-deployment-properties-reporting-services.md)   
 [Veröffentlichen von Berichten auf einem Berichtsserver](publishing-reports-to-a-report-server.md)   
 [Beispiele für URLs von veröffentlichten Berichtselementen auf einem Berichtsserver im SharePoint-Modus (SSRS)](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)   
 [Verwenden einer Office Data Connection &#40;ODC&#41; mit Berichten &#40;integrierter Reporting Services im SharePoint-Modus&#41;](../report-data/use-an-office-data-connection-odc-with-reports.md)  
  
  