---
title: Client Zertifikate auf der Berichts Server-Website (Upgrade Advisor) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 5ecce26b-99df-4109-8e51-d150d369dff7
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 5588930efbadf785e78aa115ad0021bce64bd7f7
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952602"
---
# <a name="client-certificates-on-the-report-server-web-site-upgrade-advisor"></a>Clientzertifikate auf der Berichtsserver-Website (Upgrade Advisor)
  Der Upgrade Advisor hat ein oder mehrere Clientzertifikate auf der IIS-Website gefunden, die die virtuellen Verzeichnisse des Berichtsservers oder des Berichts-Managers hostet.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Einheitlicher Modus.|  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Beschreibung  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] unterstützt die Verwendung von Clientzertifikaten zur Benutzerauthentifizierung nicht. Das Upgrade kann fortgesetzt werden, jedoch werden vom aktualisierten Berichtsserver keine Clientzertifikate verwendet.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Sie müssen eine separate Lösung verwenden, wie beispielsweise ISA Server, damit die Anforderungen für die Authentifizierung mit Clientzertifikaten erfüllt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Upgrade Advisor für &#40;Reporting Services Upgradeprobleme&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
