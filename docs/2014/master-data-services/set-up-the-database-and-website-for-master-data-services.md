---
title: Einrichten der Datenbank und Website für Master Data Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
f1_keywords:
- sql12.mds.configmanager.general.f1
ms.assetid: d50863e7-50d9-4ab8-aabb-fd68e2d132a1
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: d2d2d034424ac4564a66b40b1479acb7dc683d7c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62766548"
---
# <a name="set-up-the-database-and-website-for-master-data-services"></a>Einrichten von Datenbank und Website für Master Data Services
  Verwenden Sie den [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] , um die Datenbank und Website für [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] (MDS) einzurichten  
  
 Um die Datenbank und die Website einzurichten, führen Sie die folgenden Aufgaben aus.  
  
1.  Erstellen Sie eine Datenbank mit der **Datenbankkonfiguration** auf der Seite [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].  
  
     Weitere Informationen finden Sie unter [Datenbankkonfiguration (Seite) &#40;Konfigurations-Manager für Master Data Services&#41; ](../../2014/master-data-services/database-configuration-page-master-data-services-configuration-manager.md) und [Assistent zur Datenbankgenerierung &#40;Konfigurations-Manager für Master Data Services&#41; ](../../2014/master-data-services/create-database-wizard-master-data-services-configuration-manager.md).  
  
2.  Eine neue Website erstellen, wählen Sie die Standardwebsite oder eine andere vorhandene Website, wählen Sie mithilfe der **Webkonfiguration** auf der Seite [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]. Ordnen Sie dann die MDS-Datenbank der Webanwendung zu, die Sie ausgewählt oder erstellt haben.  
  
     Weitere Informationen finden Sie unter [Webkonfiguration (Seite) &#40;Konfigurations-Manager für Master Data Services&#41; ](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md) und [Website Dialogfeld erstellen &#40;Konfigurations-Manager für Master Data Services&#41; ](../../2014/master-data-services/create-website-dialog-box-master-data-services-configuration-manager.md).  
  
3.  (Optional) Aktivieren der Integration in Data Quality Services mithilfe der **Webkonfiguration** auf der Seite [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].  
  
     Weitere Informationen finden Sie unter [Webkonfiguration (Seite) &#40;Konfigurations-Manager für Master Data Services&#41; ](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md) und [Aktivieren von Data Quality Services-Integration mit Master Data Services](install-windows/enable-data-quality-services-integration-with-master-data-services.md).  
  
 Alternativ können Sie [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] verwenden, um Einstellungen für die der MDS-Datenbank zugeordneten Webanwendungen und -dienste festzulegen. Beispielsweise können Sie festlegen, wie häufig Daten geladen werden oder wie oft Überprüfungs-E-Mails gesendet werden. Weitere Informationen finden Sie unter [Systemeinstellungen &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Master Data Services-Datenbank](../../2014/master-data-services/master-data-services-database.md)   
 [Master Data Manager-Webanwendung](../../2014/master-data-services/master-data-manager-web-application.md)  
  
  
