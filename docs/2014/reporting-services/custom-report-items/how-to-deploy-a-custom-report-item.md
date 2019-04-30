---
title: 'Gewusst wie: Bereitstellen eines benutzerdefinierten Berichtselements | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom report items, deploying
ms.assetid: 80e97b0d-e355-4240-aebd-08cbc84089ed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2b41519ee6a6d31be33d92c8fbdf2ab503c93ec1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63265078"
---
# <a name="how-to-deploy-a-custom-report-item"></a>Gewusst wie: Bereitstellen eines benutzerdefinierten Berichtselements
  Zum Bereitstellen eines benutzerdefinierten Berichtselements in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] müssen Sie die Konfigurationsdateien des Berichtsservers ändern und die Entwurfszeit- und die Laufzeitkomponentenassemblys in die entsprechenden Anwendungsordner für den Berichts-Designer und den Berichtsserver kopieren.  
  
### <a name="to-deploy-a-custom-report-item"></a>So stellen Sie ein benutzerdefiniertes Berichtselement bereit  
  
1.  Bearbeiten Sie die Datei Rsreportdesigner.config, um die Laufzeit- und Entwurfszeitkomponenten für ein benutzerdefiniertes Berichtselement für die Verwendung im Designer zu konfigurieren. Beachten Sie dabei, dass der `ReportItemName`-Eintrag mit dem in der `CustomReportItemAttribute`-Klasse verwendeten `CustomReportItemDesigner`-Attribut übereinstimmen muss. Zum Beispiel:  
  
    ```  
    <ReportItems>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsCRI,PolygonsCRI"/>  
    </ReportItems>  
    <ReportItemDesigner>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsDesigner, PolygonsDesigner" />  
    </ReportItemDesigner>  
    <ReportItemConverter>  
       <Converter Source="Chart" Target="Polygons" Type="PolygonsCRI.PolygonsConverter, PolygonsDesigner" />  
    </ReportItemConverter>  
    ```  
  
2.  Bearbeiten Sie die Datei Rsreportserver.config, um die Laufzeitkomponente für ein benutzerdefiniertes Berichtselement zu registrieren. Zum Beispiel:  
  
    ```  
    <ReportItems>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsCRI,PolygonsCRI"/>  
    </ReportItems>  
    ```  
  
3.  Bearbeiten Sie die Datei Rsssrvpolicy.config, um ein `CodeGroup`-Objekt hinzuzufügen, das dem benutzerdefinierten Berichtselement die richtigen Berechtigungen gewährt. Zum Beispiel:  
  
    ```  
    <CodeGroup   
       class="UnionCodeGroup"   
       version="1"   
       PermissionSetName="FullTrust"  
       Description="This code group grants MyCustomReportItem.dll FullTrust permission. ">  
       <IMembershipCondition   
          class="UrlMembershipCondition"  
          version="1"  
       Url="C:\Program Files\Microsoft SQL Server\ MSRS10_50.SQLSERVER\Reporting Services\ReportServer\bin\MyCustomReportItem.dll" />  
    </CodeGroup>  
    ```  
  
4.  Kopieren Sie die Laufzeitkomponenten-DLL für ein benutzerdefiniertes Berichtselement in die Verzeichnisse %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies und \Programme\Microsoft SQL Server\MSRS10_50.SQLSERVER\Reporting Services\ReportServer\bin.  
  
5.  Kopieren Sie die Entwurfszeitkomponenten-DLL für ein benutzerdefiniertes Berichtselement in das Verzeichnis %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.  
  
## <a name="see-also"></a>Siehe auch  
 [Reporting Services-Konfigurationsdateien](../report-server/reporting-services-configuration-files.md)   
 [Custom Report Item Class Libraries (Klassenbibliotheken für ein benutzerdefiniertes Berichtselement)](custom-report-item-class-libraries.md)  
  
  
