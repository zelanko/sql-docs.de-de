---
title: Erforderliche Domänenkonten für SharePoint-Farmen (Upgrade Advisor) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 90cd6d3e-a271-4cb8-81f2-fc555b2d3cab
caps.latest.revision: 7
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: fd013ae4f7266604dde798aa76393612cd578bad
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148753"
---
# <a name="domain-accounts-required-for-sharepoint-farm-upgrade-advisor"></a>Erforderliche Domänenkonten für SharePoint-Farmen (Upgrade Advisor)
  SharePoint-Produkte, die für eine Farmumgebung konfiguriert werden, erfordern die Verwendung von Domänenkonten.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint-Modus.|  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssRS](../../includes/ssrs-md.md)]  
  
### <a name="description"></a>Description  
 SharePoint-Produkte, die für eine Farmumgebung konfiguriert werden, erfordern die Verwendung von Domänenkonten für Dienste und Datenbankverbindungen. Dies schließt das Konto ein, das Sie für das Reporting Services-Dienstkonto angegeben haben.  
  
 SharePoint 2010 Central Administration-Seiten sind eine Stelle, an der Probleme entstehen, wenn Sie kein Domänenbenutzerkonto für Reporting Services verwenden. Wenn Sie versuchen, die Reporting Services-Integration zu konfigurieren, wird Ihnen eine Fehlermeldung wie die folgende angezeigt:  
  
 "Der Berichtsserver wird auf dem integrierten NT AUTHORITY\NETWORK SERVICE-Konto ausgeführt, das von einer SharePoint-Farminstallation nicht unterstützt wird. Konfigurieren Sie den Berichtsserver neu, sodass dieser unter einem Domänenkonto ausgeführt wird."  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Für [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und frühere Versionen verwenden die Reporting Services-Konfigurations-Manager zum Ändern des Kontos, das als der Berichtsserver-Dienstkontos zugewiesen ist.  
  
#### <a name="to-change-the-service-account-from-configuration-manager"></a>So ändern Sie das Dienstkonto im Konfigurations-Manager  
  
1.  Aus der **starten** klicken Sie im Menü **Programme**, und klicken Sie dann auf **Microsoft SQL Server 2008 R2**.  
  
2.  Wählen Sie **Konfigurationstools**, und klicken Sie dann auf **Konfigurations-Manager für Reporting Services**.  
  
3.  Wählen Sie im Konfigurations-Manager die **Dienstkonto** Registerkarte.  
  
4.  Wählen Sie **Verwenden eines anderen Kontos** und geben Sie die Anmeldeinformationen für ein Domänenkonto ein.  
  
5.  Klicken Sie auf **Anwenden**.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren des Berichtsserver-Dienstkontos &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)  
  
  