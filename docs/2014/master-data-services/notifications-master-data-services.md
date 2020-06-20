---
title: Benachrichtigungen (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- notifications [Master Data Services]
- notifications [Master Data Services], about notifications
- e-mail [Master Data Services]
- e-mail [Master Data Services], about e-mail notifications
ms.assetid: d7ad32d5-9fe5-48fd-8c61-0b00c0aff082
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 6891bba64da82a1a83f5ea4a44bf3fa1f52ddd67
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84971160"
---
# <a name="notifications-master-data-services"></a>Benachrichtigungen (Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]kann konfiguriert werden, um eine e-Mail-Benachrichtigung zu senden, wenn die Geschäftsregel Überprüfung fehlschlägt oder sich der Status einer Modellversion ändert.  
  
## <a name="how-notifications-are-sent"></a>Senden von Benachrichtigungen  
 Benachrichtigungen werden in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]konfiguriert. Benachrichtigungen senden e-Mail-Nachrichten mithilfe von Datenbank-E-Mail auf der Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] , die die Datenbank hostet [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Weitere Informationen zu Datenbank-E-Mails finden Sie unter [Konfigurationsobjekte für Datenbank-E-Mail](../relational-databases/database-mail/database-mail-configuration-objects.md) in der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
## <a name="when-notifications-are-sent"></a>Zeitpunkt des Sendens von Benachrichtigungen  
 Nachdem Benachrichtigungen konfiguriert wurden, können automatisierte E-Mail-Benachrichtigungen in den folgenden Instanzen gesendet werden.  
  
|Instanz|Beschreibung|  
|--------------|-----------------|  
|Daten haben die Geschäftsregelüberprüfung nicht bestanden.|Es müssen separate Geschäftsregeln konfiguriert werden, um E-Mails zu senden, wenn ein Attributwert die Geschäftsregelüberprüfung nicht besteht. Weitere Informationen finden Sie unter [Konfigurieren von Geschäftsregeln für das Senden von Benachrichtigungen &#40;Master Data Services&#41;](configure-business-rules-to-send-notifications-master-data-services.md)konfiguriert.|  
|Der Status einer Modellversion ändert sich.|Jedes Mal, wenn sich der Status einer Modellversion ändert, erhalten Modelladministratoren automatisch eine Benachrichtigung. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).|  
  
## <a name="system-settings"></a>Systemeinstellungen  
 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] verfügt über Einstellungen, die sich auf Benachrichtigungen auswirken. Sie können diese Einstellungen in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] oder direkt in der Tabelle Systemeinstellungen der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank anpassen. Weitere Informationen finden Sie unter [Systemeinstellungen &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Konfigurieren Sie [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , um E-Mail-Benachrichtigungen zu senden.|[Konfigurieren von E-Mail-Benachrichtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/configure-email-notifications-master-data-services.md)|  
|Konfigurieren Sie [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , um Benachrichtigungen zu senden, wenn sich Attributwerte ändern.|[Konfigurieren von Geschäftsregeln für das Senden von Benachrichtigungen &#40;Master Data Services&#41;](configure-business-rules-to-send-notifications-master-data-services.md)|  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   [Geschäftsregeln &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)  
  
-   [Versionen &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md)  
  
-   [Problembehandlung für E-Mail-Benachrichtigungen (Master Data Services)](https://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-email-notifications-master-data-services.aspx)  
  
  
