---
title: Auf dem Berichts Server wurden benutzerdefinierte Berichts Elemente erkannt (Upgrade Advisor) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- custom report items, upgrading
ms.assetid: aee32006-65b2-4dfe-9570-d85a249d17b2
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 5788b94356ec887b8c83850a4cb2c47d34b7388f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "71952284"
---
# <a name="custom-report-items-were-detected-on-the-report-server-upgrade-advisor"></a>Auf dem Berichtsserver wurden benutzerdefinierte Berichtselemente erkannt (Upgrade Advisor)
  Benutzerdefinierte Berichts Elemente, die für vorherige Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] erstellt wurden, sind [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]nicht mit kompatibel. Das Upgrade kann fortgesetzt werden, jedoch werden Berichte, die das benutzerdefinierte Berichtselement verwenden, nicht wie erwartet ausgeführt. Der Upgrade Advisor hat benutzerdefinierte Berichtselemente erkannt. Das Upgrade kann fortgesetzt werden, Sie müssen jedoch die benutzerdefinierten Berichts Element Dateien manuell in den neuen Installationsordner verschieben, nachdem das Upgrade abgeschlossen wurde.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Einheitlicher Modus &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint-Modus.|  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>BESCHREIBUNG  
 Der Upgrade Advisor hat benutzerdefinierte [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Erweiterungseinstellungen in den Konfigurationsdateien gefunden. Dies ist ein Hinweis darauf, dass die Installation mindestens eine benutzerdefinierte Assembly für Berichte enthält.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Das Upgrade kann fortgesetzt werden; Sie müssen jedoch die Dateien für die benutzerdefinierten Berichtselemente nach Abschluss des Upgrades manuell in den neuen Installationsordner verschieben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Reporting Services Upgradeprobleme &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
