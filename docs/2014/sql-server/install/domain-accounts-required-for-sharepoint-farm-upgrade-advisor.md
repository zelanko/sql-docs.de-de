---
title: Erforderliche Domänen Konten für die SharePoint-Farm (Upgrade Advisor) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 90cd6d3e-a271-4cb8-81f2-fc555b2d3cab
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: c4079ea4213d7ecbec0165c32c82b3449bbb5aee
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "71952508"
---
# <a name="domain-accounts-required-for-sharepoint-farm-upgrade-advisor"></a>Erforderliche Domänenkonten für SharePoint-Farmen (Upgrade Advisor)
  SharePoint-Produkte, die für eine Farmumgebung konfiguriert werden, erfordern die Verwendung von Domänenkonten.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Im SharePoint-Modus.|  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssRS](../../includes/ssrs.md)]  
  
### <a name="description"></a>BESCHREIBUNG  
 SharePoint-Produkte, die für eine Farmumgebung konfiguriert werden, erfordern die Verwendung von Domänenkonten für Dienste und Datenbankverbindungen. Dies schließt das Konto ein, das Sie für das Reporting Services-Dienstkonto angegeben haben.  
  
 SharePoint 2010 Central Administration-Seiten sind eine Stelle, an der Probleme entstehen, wenn Sie kein Domänenbenutzerkonto für Reporting Services verwenden. Wenn Sie versuchen, die Reporting Services-Integration zu konfigurieren, wird Ihnen eine Fehlermeldung wie die folgende angezeigt:  
  
 "Der Berichtsserver wird auf dem integrierten NT AUTHORITY\NETWORK SERVICE-Konto ausgeführt, das von einer SharePoint-Farminstallation nicht unterstützt wird. Konfigurieren Sie den Berichtsserver neu, sodass dieser unter einem Domänenkonto ausgeführt wird."  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Verwenden [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Sie für und frühere Versionen die Konfigurations-Manager für Reporting Services, um das Konto zu ändern, das als Berichts Server-Dienst Konto zugewiesen ist.  
  
#### <a name="to-change-the-service-account-from-configuration-manager"></a>So ändern Sie das Dienstkonto im Konfigurations-Manager  
  
1.  Wählen Sie im **Startmenü** **Alle Programme**aus, und klicken Sie dann auf **Microsoft SQL Server 2008 R2**.  
  
2.  Wählen Sie **Konfigurationstools**aus, und klicken Sie dann auf **Konfigurations-Manager für Reporting Services**.  
  
3.  Wählen Sie in Configuration Manager die Registerkarte **Dienst Konto** aus.  
  
4.  Wählen Sie **anderes Konto verwenden** aus, und geben Sie die Anmelde Informationen eines Domänen Kontos ein.  
  
5.  Klicken Sie auf **Anwenden**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren des Berichtsserver-Dienstkontos &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)  
  
  
