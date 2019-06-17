---
title: Erforderliche Domänenkonten für SharePoint-Farmen (Upgrade Advisor) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 90cd6d3e-a271-4cb8-81f2-fc555b2d3cab
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 3e6d9802eafeea7babdcf23a3e8ea0f6b732e308
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66095512"
---
# <a name="domain-accounts-required-for-sharepoint-farm-upgrade-advisor"></a>Erforderliche Domänenkonten für SharePoint-Farmen (Upgrade Advisor)
  SharePoint-Produkte, die für eine Farmumgebung konfiguriert werden, erfordern die Verwendung von Domänenkonten.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint-Modus.|  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssRS](../../includes/ssrs.md)]  
  
### <a name="description"></a>Description  
 SharePoint-Produkte, die für eine Farmumgebung konfiguriert werden, erfordern die Verwendung von Domänenkonten für Dienste und Datenbankverbindungen. Dies schließt das Konto ein, das Sie für das Reporting Services-Dienstkonto angegeben haben.  
  
 SharePoint 2010 Central Administration-Seiten sind eine Stelle, an der Probleme entstehen, wenn Sie kein Domänenbenutzerkonto für Reporting Services verwenden. Wenn Sie versuchen, die Reporting Services-Integration zu konfigurieren, wird Ihnen eine Fehlermeldung wie die folgende angezeigt:  
  
 "Der Berichtsserver wird auf dem integrierten NT AUTHORITY\NETWORK SERVICE-Konto ausgeführt, das von einer SharePoint-Farminstallation nicht unterstützt wird. Konfigurieren Sie den Berichtsserver neu, sodass dieser unter einem Domänenkonto ausgeführt wird."  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Für [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und frühere Versionen mithilfe des Reporting Services-Konfigurations-Managers zum Ändern des Kontos, dem der Berichtsserver-Dienstkonto zugewiesen ist.  
  
#### <a name="to-change-the-service-account-from-configuration-manager"></a>So ändern Sie das Dienstkonto im Konfigurations-Manager  
  
1.  Von der **starten** , wählen Sie im Menü **Programme**, und klicken Sie dann auf **Microsoft SQL Server 2008 R2**.  
  
2.  Wählen Sie **Konfigurationstools**, und klicken Sie dann auf **Konfigurations-Manager für Reporting Services**.  
  
3.  Wählen Sie im Konfigurations-Manager die **Dienstkonto** Registerkarte.  
  
4.  Wählen Sie **verwenden ein anderes Konto** , und geben Sie die Anmeldeinformationen für ein Domänenkonto ein.  
  
5.  Klicken Sie auf **Anwenden**.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren des Berichtsserver-Dienstkontos &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)  
  
  
