---
title: SQL Server 2005-Berichts Server-Webdienst Gruppe erkannt (Upgrade Advisor) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- deployment [Reporting Services]
ms.assetid: 699d24eb-7756-4b41-9294-ef1a94b2f267
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 70be2b9c4e7abd55daaa752830a73cbe6e222659
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054667"
---
# <a name="sql-server-2005-report-server-web-service-group-detected-upgrade-advisor"></a>Berichtsserver-Webdienstgruppe von SQL Server 2005 erkannt (Upgrade Advisor)
  Der Upgrade Advisor hat festgestellt, dass die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanz einer [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Berichts Server-Webdienst Gruppe zugeordnet ist.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Einheitlicher Modus.|  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>BESCHREIBUNG  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]verwendet nicht das [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Berichts Server-Webdienst Gruppe. Beim Upgrade von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] wird diese Dienstgruppe gelöscht, und benutzerdefinierte Zugriffssteuerungslisten (Access Control Lists, ACLs) für diese Gruppe oder für Benutzer in dieser Gruppe werden nicht beibehalten.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Sichern Sie vor dem Upgrade ggf. alle benutzerdefinierten ACLs oder Benutzer, die der Berichtsserver-Webdienstgruppe von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] angehören. Hierzu können Sie das Befehlszeilen Tool **Icacls.exe** in [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] SP2 und höher oder das Befehlszeilen Tool Cacls.exe in Windows-Betriebssystemen vor [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] SP2 verwenden. Weitere Informationen zur Syntax für diese Tools finden Sie in der Windows-Produktdokumentation. Wenden Sie nach dem erfolgreichen Abschluss der Installation die benutzerdefinierten ACLs oder Benutzer auf die Berichtsserver-Windows-Gruppe von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] für Ihre Berichtsserverinstanz an. Die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Berichts Server-Windows-Gruppe hat das Format SQLServerReportServerUser $ \<*computer_name*> $ \<*instance_name*> .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Reporting Services Upgradeprobleme &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
