---
title: Virtuelles Verzeichnis weist eine nicht unterstützte Authentifizierungsmethode auf (Upgrade Advisor) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- virtual directories [Reporting Services]
ms.assetid: 216eca6f-9a66-42e1-aa54-dcf99cec9f7d
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 26420df466860677f22d39d57133568a2f02bc68
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952011"
---
# <a name="virtual-directory-has-unsupported-authentication-method-upgrade-advisor"></a>Das virtuelle Verzeichnis weist eine nicht unterstützte Authentifizierungsmethode auf (Upgrade Advisor)
  Upgrade Advisor hat im Berichts-Manager oder im virtuellen Verzeichnis des Berichtsservers eine nicht unterstützte Authentifizierungsmethode erkannt. Authentifizierungsmethoden, die von einem Upgrade nicht unterstützt werden, sind Anonymous, Digest und .NET Passport.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Einheitlicher Modus.|  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Beschreibung  
 Setup kann eine [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Installation nicht aktualisieren, die eine der folgenden Authentifizierungsmethoden verwendet  
  
-   Anonym  
  
-   Digest  
  
-   .NET Passport  
  
 Um fortzufahren, können Sie entweder die Authentifizierungsmethode ändern, die für die virtuellen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Verzeichnisse in den Internetinformationsdiensten (IIS) angegeben ist, oder die Installation migrieren. Weitere Informationen über das Migrieren einer Installation finden Sie in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Um das Upgrade fortzusetzen, ändern Sie in IIS die Authentifizierungsmethode für die virtuellen Verzeichnisse ReportServer und Reports. Weitere Informationen zum Ändern der Authentifizierungsmethode in IIS finden Sie in der IIS-Dokumentation. Führen Sie nach dem Ändern der Authentifizierungsmethode für die virtuellen Verzeichnisse von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] den Upgrade Advisor erneut aus, um zu bestätigen, dass keine weiteren Upgradeprobleme vorliegen.  
  
## <a name="see-also"></a>Siehe auch  
 [Upgrade Advisor für &#40;Reporting Services Upgradeprobleme&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
