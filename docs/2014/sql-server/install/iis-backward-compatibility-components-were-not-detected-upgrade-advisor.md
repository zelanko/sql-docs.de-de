---
title: IIS-abwärts Kompatibilitäts Komponenten wurden nicht erkannt (Upgrade Advisor) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- IIS [Reporting Services]
ms.assetid: e794185a-0a77-480a-9aea-d09f8760a6b8
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: dbf5686d4a947cb8629675368c59c8039c93835e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "71952501"
---
# <a name="iis-backward-compatibility-components-were-not-detected-upgrade-advisor"></a>IIS-Abwärtskompatibilitätskomponenten wurden nicht erkannt (Upgrade Advisor)
  Upgrade Advisor hat keine IIS-Komponenten und -Einstellungen erkannt, die Informationen bereitstellen, mit denen Setup neue [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-URLs erstellt.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Einheitlicher Modus.|  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>BESCHREIBUNG  
 IIS enthält Komponenten, die Informationen über die virtuellen Verzeichnisse des Berichtsservers und des Berichts-Managers bereitstellen. Diese Komponenten sind nicht auf dem Computer mit dem Berichtsserver installiert. Das Upgrade kann fortgesetzt werden, die URLs für den Berichtsserver oder den Berichts-Manager werden beim Upgrade jedoch nicht neu erstellt.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Verwenden Sie nach Abschluss des Upgrades das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Konfigurationstool, um die URLs für den Berichtsserver oder den Berichts-Manager festzulegen. Verwenden Sie IIS-Manager, um die virtuellen Verzeichnisse zu entfernen, die Sie nicht mehr benötigen.  
  
 Weitere Informationen finden Sie unter [Konfigurieren einer URL &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der-Online Dokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Reporting Services Upgradeprobleme &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
