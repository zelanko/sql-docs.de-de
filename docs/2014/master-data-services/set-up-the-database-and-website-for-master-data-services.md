---
title: Einrichten der Datenbank und Website für Master Data Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
f1_keywords:
- sql12.mds.configmanager.general.f1
ms.assetid: d50863e7-50d9-4ab8-aabb-fd68e2d132a1
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 478dea9095fe22a437aecf138c22374b5a70885b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66054095"
---
# <a name="set-up-the-database-and-website-for-master-data-services"></a>Einrichten von Datenbank und Website für Master Data Services
  Verwenden Sie den [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] , um die Datenbank und Website für [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] (MDS) einzurichten  
  
 Um die Datenbank und die Website einzurichten, führen Sie die folgenden Aufgaben aus.  
  
1.  Erstellen Sie eine Datenbank mithilfe der Seite **Daten Bank Konfiguration** in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].  
  
     Weitere Informationen finden Sie auf der [Seite Daten Bank Konfiguration &#40;Konfigurations-Manager für Master Data Services&#41;](../../2014/master-data-services/database-configuration-page-master-data-services-configuration-manager.md) und [Assistent zum Erstellen einer Datenbank &#40;Konfigurations-Manager für Master Data Services&#41;](../../2014/master-data-services/create-database-wizard-master-data-services-configuration-manager.md).  
  
2.  Erstellen Sie eine neue Website, wählen Sie die Standard Website aus, oder wählen Sie eine andere vorhandene Website mithilfe der [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]Seite **Webkonfiguration** in aus. Ordnen Sie dann die MDS-Datenbank der Webanwendung zu, die Sie ausgewählt oder erstellt haben.  
  
     Weitere Informationen finden Sie unter [webkonfigurationsseite &#40;Konfigurations-Manager für Master Data Services&#41;](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md) und [Dialog Feld "Website erstellen" &#40;Konfigurations-Manager für Master Data Services&#41;](../../2014/master-data-services/create-website-dialog-box-master-data-services-configuration-manager.md).  
  
3.  Optionale Aktivieren Sie die Integration in Data Quality Services mithilfe der Seite **Webkonfiguration** in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].  
  
     Weitere Informationen finden Sie unter [Web Configuration page &#40;Konfigurations-Manager für Master Data Services&#41;](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md) und [Aktivieren der Data Quality Services-Integration in Master Data Services](install-windows/enable-data-quality-services-integration-with-master-data-services.md).  
  
 Alternativ können Sie [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] verwenden, um Einstellungen für die der MDS-Datenbank zugeordneten Webanwendungen und -dienste festzulegen. Beispielsweise können Sie festlegen, wie häufig Daten geladen werden oder wie oft Überprüfungs-E-Mails gesendet werden. Weitere Informationen finden Sie unter [Systemeinstellungen &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Master Data Services Datenbank](../../2014/master-data-services/master-data-services-database.md)   
 [Master Data Manager-Webanwendung [Master Data Services]](../../2014/master-data-services/master-data-manager-web-application.md)  
  
  
