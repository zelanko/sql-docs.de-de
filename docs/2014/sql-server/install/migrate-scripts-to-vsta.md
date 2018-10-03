---
title: Migrieren von Skripts zu VSTA | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- SSIS Script task, converting scripts
- Script component [Integration Services], converting scripts
- Script task [Integration Services], converting scripts
- SSIS Script component, converting scripts
ms.assetid: d685098b-86a1-46bf-939a-63d56951e009
author: mashamsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b23d85aa038acae6631dedf64417c65e745baf90
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48084432"
---
# <a name="migrate-scripts-to-vsta"></a>Migrieren von Skripts zu VSTA
  Wenn Sie ein upgrade [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Pakete [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] migriert die Skripts in allen Skripttasks und Skriptkomponenten zu [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA). VSTA ist die von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] verwendete Skriptumgebung. In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], die skriptumgebung für [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ist [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] für Applikationen (VSA).  
  
 Wenn die Skripts in den Skripttasks oder Skriptkomponenten auf Schnittstellen verweisen, müssen Sie diese Verweise ggf. ändern, bevor Sie das Paket aktualisieren. Andernfalls tritt beim Aktualisieren des Pakets oder beim Überprüfen der Skripts je nach verwendeter Upgrademethode ein Fehler auf. Um diese Verweise zu ändern, ersetzen Sie Verweise auf IDTS*Xxx*90-Schnittstellen durch Verweise auf die entsprechenden IDTS*Xxx*100-Schnittstellen.  
  
 Weitere Informationen zum Migrieren von Skripts und Pakete aktualisieren, finden Sie unter [Aktualisieren von Integration Services-Paketen](../../integration-services/install-windows/upgrade-integration-services-packages.md).  
  
## <a name="understanding-migration-failures"></a>Grundlegendes zu Migrationsfehlern  
 Beim Migrieren der Skripts kann aus einem der folgenden Gründe ein Fehler auftreten:  
  
-   Der Einstiegspunkt für das VSA-Skript wurde umbenannt.  
  
     Mit dem Einstiegspunkt wird die Methode in der `ScriptMain`-Klasse im VSTA-Projekt angegeben, die die [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Laufzeit als Einstiegspunkt in den Code des Skripttasks aufruft. Die `ScriptMain` Klasse ist die Standardklasse, die von die Skriptvorlagen generiert.  
  
-   Das VSA-Skript weist keinen Einstiegspunkt oder mehrere Einstiegspunkte auf.  
  
-   Es konnten keine Assemblyverweise hinzugefügt werden.  
  
-   Die `ScriptMain`-Klasse wurde so geändert, dass sie neben der `ScriptObjectModelSSIS`-Klasse von anderen Klassen erbt. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] unterstützt keine mehrfachvererbung.  
  
 Sie können nicht konvertiert werden ein VSA-Skript, das verwendet [!INCLUDE[vbprvblong](../../includes/vbprvblong-md.md)] in ein VSTA-Skript, die verwendet [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)]. Allerdings können Sie erstellen ein neues VSTA-Skript, das verwendet [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)]. Weitere Informationen finden Sie unter [Coding and Debugging the Script Task](../../integration-services/control-flow/script-task.md) (Codieren und Debuggen des Skripttasks) und [Coding and Debugging the Script Component](../../integration-services/data-flow/transformations/script-component.md) (Codieren und Debuggen der Skriptkomponente).  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von Paketen mit Skripts](../../relational-databases/server-management-objects-smo/tasks/scripting.md)  
  
  
