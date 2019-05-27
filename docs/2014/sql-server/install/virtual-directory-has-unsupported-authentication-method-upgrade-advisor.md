---
title: Virtuelles Verzeichnis weist eine nicht unterstützte Authentifizierungsmethode (Upgrade Advisor) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- virtual directories [Reporting Services]
ms.assetid: 216eca6f-9a66-42e1-aa54-dcf99cec9f7d
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 992e0f125d80a4735a356a853dab55439149e7ba
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66091057"
---
# <a name="virtual-directory-has-unsupported-authentication-method-upgrade-advisor"></a>Das virtuelle Verzeichnis weist eine nicht unterstützte Authentifizierungsmethode auf (Upgrade Advisor)
  Upgrade Advisor hat im Berichts-Manager oder im virtuellen Verzeichnis des Berichtsservers eine nicht unterstützte Authentifizierungsmethode erkannt. Authentifizierungsmethoden, die von einem Upgrade nicht unterstützt werden, sind Anonymous, Digest und .NET Passport.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Einheitlicher Modus.|  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 Setup kann eine [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Installation nicht aktualisieren, die eine der folgenden Authentifizierungsmethoden verwendet  
  
-   Anonym  
  
-   Digest  
  
-   .NET Passport  
  
 Um fortzufahren, können Sie entweder die Authentifizierungsmethode ändern, die für die virtuellen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Verzeichnisse in den Internetinformationsdiensten (IIS) angegeben ist, oder die Installation migrieren. Weitere Informationen über das Migrieren einer Installation finden Sie in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Um das Upgrade fortzusetzen, ändern Sie in IIS die Authentifizierungsmethode für die virtuellen Verzeichnisse ReportServer und Reports. Weitere Informationen zum Ändern der Authentifizierungsmethode in IIS finden Sie in der IIS-Dokumentation. Führen Sie nach dem Ändern der Authentifizierungsmethode für die virtuellen Verzeichnisse von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] den Upgrade Advisor erneut aus, um zu bestätigen, dass keine weiteren Upgradeprobleme vorliegen.  
  
## <a name="see-also"></a>Siehe auch  
 [Upgradeprobleme bei Reporting Services &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
