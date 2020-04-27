---
title: Migrieren von Skripts zu VSTA | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- SSIS Script task, converting scripts
- Script component [Integration Services], converting scripts
- Script task [Integration Services], converting scripts
- SSIS Script component, converting scripts
ms.assetid: d685098b-86a1-46bf-939a-63d56951e009
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: cb44a7b635e24c0c2e3266c1cca98a9c4f6a347c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66093987"
---
# <a name="migrate-scripts-to-vsta"></a>Migrieren von Skripts zu VSTA
  Wenn Sie Pakete [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]aktualisieren, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] werden die Skripts in allen Skript Tasks oder Skript Komponenten zu [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) migriert. VSTA ist die von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] verwendete Skriptumgebung. In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] handelt es sich [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] bei der Skript Umgebung für um Anwendungen (VSA).  
  
 Wenn die Skripts in den Skripttasks oder Skriptkomponenten auf Schnittstellen verweisen, müssen Sie diese Verweise ggf. ändern, bevor Sie das Paket aktualisieren. Andernfalls tritt beim Aktualisieren des Pakets oder beim Überprüfen der Skripts je nach verwendeter Upgrademethode ein Fehler auf. Um diese Verweise zu ändern, ersetzen Sie die Verweise auf IDTs*xxx*90-Schnittstellen durch Verweise auf die entsprechenden IDTs*xxx*100-Schnittstellen.  
  
 Weitere Informationen zum Migrieren von Skripts und Upgradepaketen finden Sie unter [Aktualisieren von Integration Services Paketen](../../integration-services/install-windows/upgrade-integration-services-packages.md).  
  
## <a name="understanding-migration-failures"></a>Grundlegendes zu Migrationsfehlern  
 Beim Migrieren der Skripts kann aus einem der folgenden Gründe ein Fehler auftreten:  
  
-   Der Einstiegspunkt für das VSA-Skript wurde umbenannt.  
  
     Mit dem Einstiegspunkt wird die Methode in der `ScriptMain`-Klasse im VSTA-Projekt angegeben, die die [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Laufzeit als Einstiegspunkt in den Code des Skripttasks aufruft. Die `ScriptMain` -Klasse ist die Standardklasse, die von den Skript Vorlagen generiert wird.  
  
-   Das VSA-Skript weist keinen Einstiegspunkt oder mehrere Einstiegspunkte auf.  
  
-   Es konnten keine Assemblyverweise hinzugefügt werden.  
  
-   Die `ScriptMain`-Klasse wurde so geändert, dass sie neben der `ScriptObjectModelSSIS`-Klasse von anderen Klassen erbt. [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] unterstützt keine mehrfache Vererbung.  
  
 Ein VSA-Skript, das verwendet [!INCLUDE[vbprvblong](../../includes/vbprvblong-md.md)] , kann nicht in ein VSTA- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)]Skript konvertiert werden, das verwendet. Sie können jedoch ein neues VSTA-Skript erstellen, das [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)]verwendet. Weitere Informationen finden Sie unter [Coding and Debugging the Script Task](../../integration-services/control-flow/script-task.md) (Codieren und Debuggen des Skripttasks) und [Coding and Debugging the Script Component](../../integration-services/data-flow/transformations/script-component.md) (Codieren und Debuggen der Skriptkomponente).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweitern von Paketen mit Skripts](../../relational-databases/server-management-objects-smo/tasks/scripting.md)  
  
  
