---
title: 'Gewusst wie: Bereitstellen eines benutzerdefinierten Berichtselements | Microsoft-Dokumentation'
description: In diesem Artikel erfahren Sie, wie Sie ein benutzerdefiniertes Berichtselement bereitstellen. Außerdem ändern Sie die Konfigurationsdateien des Berichtsservers und kopieren die Komponentenassemblys in die entsprechenden Ordner.
ms.date: 03/18/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: custom-report-items
ms.topic: reference
helpviewer_keywords:
- custom report items, deploying
ms.assetid: 80e97b0d-e355-4240-aebd-08cbc84089ed
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 31347efeda4805d4faffc993c164441cba1697c4
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "80216922"
---
# <a name="how-to-deploy-a-custom-report-item"></a>Gewusst wie: Bereitstellen eines benutzerdefinierten Berichtselements
  Zum Bereitstellen eines benutzerdefinierten Berichtselements in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] müssen Sie die Konfigurationsdateien des Berichtsservers ändern und die Entwurfszeit- und die Laufzeitkomponentenassemblys in die entsprechenden Anwendungsordner für den Berichts-Designer und den Berichtsserver kopieren.  
  
### <a name="to-deploy-a-custom-report-item"></a>So stellen Sie ein benutzerdefiniertes Berichtselement bereit  
  
1.  Bearbeiten Sie die Datei Rsreportdesigner.config, um die Laufzeit- und Entwurfszeitkomponenten für ein benutzerdefiniertes Berichtselement für die Verwendung im Designer zu konfigurieren. Beachten Sie, dass der **ReportItemName**-Eintrag mit dem **CustomReportItemAttribute**-Attribut, das in Ihrer **CustomReportItemDesigner**-Klasse verwendet wird, übereinstimmen muss. Beispiel:  
  
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
  
2.  Bearbeiten Sie die Datei Rsreportserver.config, um die Laufzeitkomponente für ein benutzerdefiniertes Berichtselement zu registrieren. Beispiel:  
  
    ```  
    <ReportItems>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsCRI,PolygonsCRI"/>  
    </ReportItems>  
    ```  
  
3.  Bearbeiten Sie die Datei „Rsssrvpolicy.config“, um eine **CodeGroup** hinzuzufügen, die dem benutzerdefinierten Berichtselement die richtigen Berechtigungen gewährt. Beispiel:  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Reporting Services-Konfigurationsdateien](../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [Custom Report Item Class Libraries (Klassenbibliotheken für ein benutzerdefiniertes Berichtselement)](../../reporting-services/custom-report-items/custom-report-item-class-libraries.md)  
  
  
