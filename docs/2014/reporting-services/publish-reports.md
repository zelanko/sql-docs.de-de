---
title: Veröffentlichen von Berichten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], publishing
- publishing reports [Reporting Services]
ms.assetid: ef5a514e-e818-4041-a8b0-15835f9a046b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 86ab056f18e69b0b264525377efb0d257ebc2b95
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66108028"
---
# <a name="publish-reports"></a>Veröffentlichen von Berichten
  Von[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]aus können Sie entweder alle Berichte und freigegebenen Datenquellen in einem Berichtsserverprojekt auf einem Berichtsserver veröffentlichen, indem Sie das Projekt bereitstellen, oder Sie können einen einzelnen Bericht veröffentlichen. Bevor Sie einen Bericht veröffentlichen können, müssen Sie die URL des Zielberichtsservers angeben. Weitere Informationen finden Sie unter [Festlegen von Bereitstellungseigenschaften &#40;Reporting Services&#41;](tools/set-deployment-properties-reporting-services.md).  
  
 Sie können die [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] -Version von [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] verwenden, um sowohl [!INCLUDE[ssRSversion2005](../includes/ssrsversion2005-md.md)] -Berichte als auch [!INCLUDE[ssRSversion10](../includes/ssrsversion10-md.md)] -Berichte zu öffnen, zu ändern, in der Vorschau anzuzeigen, zu speichern und zu veröffentlichen. Weitere Informationen finden Sie unter [Bereitstellung und Versionsunterstützung in SQL Server Data Tools &#40;SSRS&#41;](tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md)enthalten.  
  
### <a name="to-publish-all-reports-in-a-project"></a>So veröffentlichen Sie alle Berichte in einem Projekt  
  
-   Klicken Sie im Menü **Erstellen** auf **Berichtsprojektname>\< bereitstellen**. Sie können auch im Projektmappen-Explorer mit der rechten Maustaste auf das Berichtsobjekt klicken. Klicken Sie dann auf **Bereitstellen**. Den Status des Veröffentlichungsvorgangs sehen Sie im Ausgabefenster.  
  
    > [!NOTE]  
    >  Wenn Sie ein Berichtsserverprojekt bereitstellen, werden die freigegebenen Datenquellen im Berichtsprojekt ebenfalls bereitgestellt.  
  
### <a name="to-publish-a-single-report"></a>So veröffentlichen Sie einen einzelnen Bericht  
  
-   Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Bericht, und klicken Sie auf **Bereitstellen**. Den Status des Veröffentlichungsvorgangs sehen Sie im Ausgabefenster.  
  
    > [!NOTE]  
    >  Wenn Sie einen Bericht veröffentlichen, müssen Sie auch die freigegebenen Datenquellen bereitstellen, die vom Bericht verwendet werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Veröffentlichen von Datenquellen und Berichten](reports/publishing-data-sources-and-reports.md)   
 [Anzeigen einer Vorschau für Berichte](reports/previewing-reports.md)   
 [Veröffentlichen von Berichten auf einem Berichts Server](reports/publishing-reports-to-a-report-server.md)   
 [Suchen, anzeigen und Verwalten von Berichten &#40;Berichts-Generator und SSRS &#41;](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [Exportieren von Berichten &#40;Berichts-Generator und SSRS&#41;](report-builder/export-reports-report-builder-and-ssrs.md)  
  
  
