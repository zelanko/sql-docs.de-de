---
title: Webkonfiguration (Seite im Konfigurations-Manager für Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
f1_keywords:
- sql12.mds.configmanager.webconfigpg.f1
ms.assetid: 7b900778-0169-4e42-9faf-98dc1c01313e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f5ebc7284b6d51f17bcddde24a0934827466e02c
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84960550"
---
# <a name="web-configuration-page-master-data-services-configuration-manager"></a>Webkonfiguration (Seite im Konfigurations-Manager für Master Data Sevices)
  Verwenden Sie die Seite **Webkonfiguration** , um eine neue Website zu erstellen oder eine neue Website oder eine Webanwendung zu erstellen. Nachdem Sie eine [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Webanwendung ausgewählt haben, können Sie die [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank der Anwendung angeben und Data Quality Services aktivieren.  
  
## <a name="configure-the-web-application"></a>Konfigurieren der Webanwendung  
  
|Name des Steuerelements|Beschreibung|  
|------------------|-----------------|  
|**Website**|Erstellen Sie eine neue Website, wählen Sie die Standardwebsite aus oder wählen Sie eine andere verfügbare Website aus (wenn aufgelistet). Diese Liste zeigt die Websites an, die in Internet Information Services (IIS) auf dem lokalen Computer definiert sind. Wenn Sie eine neue Website erstellen, wird automatisch eine neue Webanwendung erstellt. Wenn Sie den Standard oder eine andere vorhandene Website auswählen, müssen Sie manuell eine Anwendung erstellen.|  
|**Webanwendung**|Wählen Sie eine [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Webanwendung zur Konfiguration aus. In diesem Feld werden nur die [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Webanwendungen in der ausgewählten Website angezeigt.<br /><br /> Wenn nichts angezeigt wird, klicken Sie auf **Anwendung erstellen** , um eine Website zu erstellen.|  
|**Anwendung erstellen**|Öffnet das Dialogfeld **Webanwendung erstellen** , in dem Sie eine [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Webanwendung in der ausgewählten Website erstellen. Diese Schaltfläche wird nur aktiviert, wenn die ausgewählte Website über keine Stammwebanwendung verfügt, die als [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Webanwendung konfiguriert ist.|  
  
## <a name="associate-application-with-database"></a>Zuordnen einer Anwendung zu einer Datenbank  
  
|Name des Steuerelements|Beschreibung|  
|------------------|-----------------|  
|**Auswählen**|Öffnet das Dialogfeld **Verbindung mit Server herstellen** , in dem Sie eine Verbindung mit einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz herstellen und eine [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank auswählen, die mit der ausgewählten [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Webanwendung verknüpft werden soll.|  
|**SQL Server-Instanz**|Zeigt den Namen der ausgewählten [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz an, auf der die [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank gehostet wird. Es wird erst ein Eintrag angezeigt, nachdem Sie eine Verbindung mit einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz hergestellt und eine Datenbank ausgewählt haben.|  
|**Datenbank**|Zeigt den Namen der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank an, die der ausgewählten [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Webanwendung zugeordnet ist. Es wird erst ein Eintrag angezeigt, nachdem Sie eine Verbindung mit einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz hergestellt und eine Datenbank ausgewählt haben.|  
  
## <a name="enable-dqs-integration"></a>Aktivieren der DQS-Integration  
  
|Name des Steuerelements|Beschreibung|  
|------------------|-----------------|  
|**Integration in Data Quality Services aktivieren**|Aktivieren Sie diese Option, um die in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]. Weitere Informationen finden Sie unter [Aktivieren der Data Quality Services-Integration in Master Data Services](install-windows/enable-data-quality-services-integration-with-master-data-services.md).|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Einrichten der Datenbank und Website für Master Data Services](../../2014/master-data-services/set-up-the-database-and-website-for-master-data-services.md)   
 [Webanwendungs Anforderungen &#40;Master Data Services&#41;](install-windows/web-application-requirements-master-data-services.md)   
 [Erstellen Sie eine Master Data Manager-Webanwendung &#40;Master Data Services&#41;](install-windows/create-a-master-data-manager-web-application-master-data-services.md)   
 [MDS 2014 und Fehler "Dienst nicht verfügbar"](https://blogs.msdn.com/b/womeninanalytics/archive/2015/08/19/mds-2014-and-service-unavailable-error.aspx)  
  
  
