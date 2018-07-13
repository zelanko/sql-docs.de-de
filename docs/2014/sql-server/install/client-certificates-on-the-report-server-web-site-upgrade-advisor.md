---
title: Clientzertifikate auf den Berichtsserver-Website (Upgrade Advisor) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 5ecce26b-99df-4109-8e51-d150d369dff7
caps.latest.revision: 12
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 93128f60320fbcf82a3368d6008fe647497fa4dc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37270286"
---
# <a name="client-certificates-on-the-report-server-web-site-upgrade-advisor"></a>Clientzertifikate auf der Berichtsserver-Website (Upgrade Advisor)
  Der Upgrade Advisor hat ein oder mehrere Clientzertifikate auf der IIS-Website gefunden, die die virtuellen Verzeichnisse des Berichtsservers oder des Berichts-Managers hostet.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Einheitlicher Modus.|  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] unterstützt die Verwendung von Clientzertifikaten zur Benutzerauthentifizierung nicht. Das Upgrade kann fortgesetzt werden, jedoch werden vom aktualisierten Berichtsserver keine Clientzertifikate verwendet.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Sie müssen eine separate Lösung verwenden, wie beispielsweise ISA Server, damit die Anforderungen für die Authentifizierung mit Clientzertifikaten erfüllt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Upgradeprobleme bei Reporting Services &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
