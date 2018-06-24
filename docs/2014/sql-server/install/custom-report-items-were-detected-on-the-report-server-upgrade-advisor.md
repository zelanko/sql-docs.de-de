---
title: Benutzerdefinierte Berichtselemente erkannt wurden, auf dem Berichtsserver (Upgrade Advisor) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- custom report items, upgrading
ms.assetid: aee32006-65b2-4dfe-9570-d85a249d17b2
caps.latest.revision: 14
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 6395fceff333f29c1fa7d5dbc29ecad7bebdadd4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047986"
---
# <a name="custom-report-items-were-detected-on-the-report-server-upgrade-advisor"></a>Auf dem Berichtsserver wurden benutzerdefinierte Berichtselemente erkannt (Upgrade Advisor)
  Benutzerdefinierte Berichtselemente, die für frühere Versionen von erstellte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sind nicht kompatibel mit [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Das Upgrade kann fortgesetzt werden, jedoch werden Berichte, die das benutzerdefinierte Berichtselement verwenden, nicht wie erwartet ausgeführt. Der Upgrade Advisor hat benutzerdefinierte Berichtselemente erkannt. Das Upgrade kann fortgesetzt, aber Sie müssen benutzerdefinierte Berichtsdatei Element manuell in den neuen Installationsordner verschieben, nach Abschluss des Upgrades.  
  
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
  
  