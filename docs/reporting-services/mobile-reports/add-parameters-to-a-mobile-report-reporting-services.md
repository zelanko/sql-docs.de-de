---
title: Hinzufügen von Parametern zu einem mobilen Bericht | Reporting Services | Microsoft-Dokumentation
description: Mobile Reporting Services-Berichte können über Parameter verfügen, damit Leser Ihre Berichte filtern können. Solche Berichte können als Ziel für einen Drillthrough verwendet werden.
ms.date: 07/30/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: mobile-reports
ms.topic: conceptual
ms.assetid: 113cb057-deec-40eb-abc8-f35d3900eaa6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 36bf305d4685f18e1c6df9129716ae9de84d4f84
ms.sourcegitcommit: ea0bf89617e11afe85ad85309e0ec731ed265583
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92907288"
---
# <a name="add-parameters-to-a-mobile-report--reporting-services"></a>Hinzufügen von Parametern zu einem mobilen Bericht | Reporting Services
Sie können einen mobilen [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)]-Bericht mit Parametern erstellen, sodass Sie und die Leser des Berichts Ihre Berichte filtern können. Ein Bericht mit Parametern kann als Ziel eines [Drillthroughs aus einem Quellbericht](../../reporting-services/mobile-reports/add-drillthrough-from-a-mobile-report-to-other-mobile-reports-or-urls.md) verwendet werden. 

Beginnen Sie mit einem freigegebenen Dataset mit mindestens einem Parameter, um einen mobilen Bericht mit Parametern zu erstellen. Erfahren Sie mehr über das [Erstellen von Parametern in einem freigegebenen Dataset](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md). Mobile Berichte unterstützen keine NULL-Werte für Standardparameter, deshalb müssen Sie sicherstellen, dass Ihre Parameter andere Standardwerte als NULL verwenden.

Nachdem Sie einem mobilen Bericht Parameter hinzugefügt haben, erstellen Sie eine URL zum [Öffnen des Berichts mit Abfragezeichenfolgenparametern](../../reporting-services/mobile-reports/open-a-mobile-report-with-specific-query-string-parameters-reporting-services.md). 

1. Wählen Sie auf der oberen Leiste des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion.md)] -Webportals **Neu** > **Mobiler Bericht** aus.  
  
   ![PBI_SSMRP_NewMenu](../../reporting-services/mobile-reports/media/pbi-ssmrp-newmenu.png)  
     
2. Wählen Sie in der linken oberen Ecke von **die Registerkarte** Daten [!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-long.md)]aus.   
  
3. Wählen Sie in der oberen rechten Ecke **Daten hinzufügen** aus.  
  
4. Wählen Sie **Berichtsserver** aus, wählen Sie anschließend einen Server aus.  
  
5. Navigieren Sie zu den freigegebenen Datasets auf dem Server, und wählen Sie eines, das über Parameter verfügt.  
  
   Im Raster werden die Daten im Dataset angezeigt. Der grüne Kreis mit Klammern **{ }** kennzeichnet ein Dataset mit einem Parameter.  
     
   ![SSMRP_PforParam](../../reporting-services/mobile-reports/media/ssmrp-pforparam.png)  
  
6. Wählen Sie das Rädchen auf der Registerkarte aus, und wählen Sie dann **Param {}** aus.  
  
   ![SSMRP_ParamWheel](../../reporting-services/mobile-reports/media/ssmrp-paramwheel.png)  
  
7. Wählen Sie das Berichtselement, das Werte an den Parameter übergeben wird.  
  
   ![SSMRP_SetParam](../../reporting-services/mobile-reports/media/ssmrp-setparam.png)  
     
8. Wählen Sie **Vorschau** aus, um zu sehen, wie der Bericht dargestellt wird. In diesem Bericht verwendet die Auswahlliste den „Category“-Parameter.

   ![Screenshot der Vorschau des Berichts mit hervorgehobener Auswahlliste 1](../../reporting-services/mobile-reports/media/sql-server-mobile-report-publisher-selection-list-view-no-selection.png) 
   
9. Wenn Sie einen Wert in der Auswahlliste auswählen, wird der Bericht nach diesem Wert gefiltert, in diesem Fall „Accessories“.

   ![Screenshot der Vorschau des Berichts mit hervorgehobener Auswahlliste 1 und ausgewählter Option „Accessories“](../../reporting-services/mobile-reports/media/sql-server-mobile-report-publisher-selection-list-category-selected.png)   
  
### <a name="see-also"></a>Weitere Informationen  
-  [Open a mobile report with specific query string parameters (Öffnen eines mobilen Berichts mit bestimmten Abfragezeichenfolgenparametern)](../../reporting-services/mobile-reports/open-a-mobile-report-with-specific-query-string-parameters-reporting-services.md)
-  [Add drillthrough from a mobile report to other mobile reports or URLs (Drillthrough zu anderen mobilen Berichten oder URLs aus einem mobilen Bericht hinzufügen)](../../reporting-services/mobile-reports/add-drillthrough-from-a-mobile-report-to-other-mobile-reports-or-urls.md)
-  [Erstellen eines freigegebenen Datasets oder eingebetteten Datasets (Berichts-Generator und SSRS)](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)
- [Erstellen und Veröffentlichen von mobilen Berichten mit dem Publisher für mobile Berichte von SQL Server](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
  
  

