---
title: Benutzerdefinierte Berichtselemente erkannt wurden, auf dem Berichtsserver (Upgrade Advisor) | Microsoft-Dokumentation
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
- custom report items, upgrading
ms.assetid: aee32006-65b2-4dfe-9570-d85a249d17b2
caps.latest.revision: 14
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 2f7548a78ebbb4d7d01f8bfb9e796d32a9b3b28d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37261906"
---
# <a name="custom-report-items-were-detected-on-the-report-server-upgrade-advisor"></a>Auf dem Berichtsserver wurden benutzerdefinierte Berichtselemente erkannt (Upgrade Advisor)
  Benutzerdefinierte Berichtselemente, die für frühere Versionen von erstellten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sind nicht kompatibel mit [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Das Upgrade kann fortgesetzt werden, jedoch werden Berichte, die das benutzerdefinierte Berichtselement verwenden, nicht wie erwartet ausgeführt. Der Upgrade Advisor hat benutzerdefinierte Berichtselemente erkannt. Das Upgrade kann fortgesetzt, aber Sie müssen den benutzerdefinierten Berichtsdateien manuell in den neuen Installationsordner verschieben, nach Abschluss des Upgrades.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**: [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus|  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 Der Upgrade Advisor hat benutzerdefinierte [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Erweiterungseinstellungen in den Konfigurationsdateien gefunden. Dies ist ein Hinweis darauf, dass die Installation mindestens eine benutzerdefinierte Assembly für Berichte enthält.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Das Upgrade kann fortgesetzt werden; Sie müssen jedoch die Dateien für die benutzerdefinierten Berichtselemente nach Abschluss des Upgrades manuell in den neuen Installationsordner verschieben.  
  
## <a name="see-also"></a>Siehe auch  
 [Upgradeprobleme bei Reporting Services &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
