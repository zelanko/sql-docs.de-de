---
title: Architektur des benutzerdefinierten Berichtselements | Microsoft-Dokumentation
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: custom-report-items
ms.topic: reference
helpviewer_keywords:
- custom report items, architecture
ms.assetid: 2a88ea46-c9f8-4dd7-aad1-16de11da4f06
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 2c9cf8ad14706b3e344ff6810bfae3ce84af2c32
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52395403"
---
# <a name="custom-report-item-architecture"></a>Architektur des benutzerdefinierten Berichtselements
  Ein benutzerdefiniertes Berichtselement ist eine Erweiterung von RDL (Report Definition Language), mit dem Entwickler Funktionen hinzufügen können, die ursprünglich nicht in RDL unterstützt werden oder mit denen die Funktionen bestehender Steuerelemente erweitert werden. Es gibt zwei Hauptkomponenten in einem benutzerdefinierten Berichtselement: die Laufzeitkomponente und die Entwurfszeitkomponente. Diese Komponenten sind als [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-Assemblys implementiert und können in jeder CLS-konformen Sprache geschrieben werden.  
  
## <a name="the-run-time-component"></a>Die Laufzeitkomponente  
 Die Laufzeitkomponente für ein benutzerdefiniertes Berichtselement wird vom Berichtsprozessor zur Laufzeit aufgerufen. Die Laufzeitkomponente akzeptiert Daten, die vom Berichtsprozessor zur Laufzeit übergeben werden, verarbeitet diese Daten und gibt ein Bild zurück, das das gerenderte, benutzerdefinierte Berichtselement enthält.  
  
 ![Laufzeitkomponente für ein benutzerdefiniertes Berichtselement](../../reporting-services/custom-report-items/media/customreportitemrun-timecomponentarchitecture.gif "Custom report item run-time component")  
  
## <a name="the-design-time-component"></a>Die Entwurfszeitkomponente  
 Über die Entwurfszeitkomponente kann das benutzerdefinierte Berichtselement in der Berichts-Designer-Schnittstelle in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] definiert und bearbeitet werden. Die Entwurfszeitkomponente besteht aus mehreren Untersteuerungselementen, die das Aussehen und die Eigenschaften des benutzerdefinierten Berichtselements in der Entwurfsumgebung steuern.  
  
 ![Entwurfszeitkomponente für ein benutzerdefiniertes Berichtselement](../../reporting-services/custom-report-items/media/customreportitemdesign-timecomponentarchitecture.gif "Custom report item design-time component")  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Erstellen einer Laufzeitkomponente für ein benutzerdefiniertes Berichtselement](../../reporting-services/custom-report-items/creating-a-custom-report-item-run-time-component.md)   
 [Erstellen einer Entwurfszeitkomponente für ein benutzerdefiniertes Berichtselement](../../reporting-services/custom-report-items/creating-a-custom-report-item-design-time-component.md)   
 [Vorgehensweise: Bereitstellen eines benutzerdefinierten Berichtselements](../../reporting-services/custom-report-items/how-to-deploy-a-custom-report-item.md)  
  
  
