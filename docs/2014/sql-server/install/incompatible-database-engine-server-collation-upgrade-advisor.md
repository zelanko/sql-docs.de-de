---
title: Nicht kompatible Datenbank-Engine Server-Sortierung (Upgrade Advisor) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 80f499d6-2c90-49eb-a5b3-0bb5b7faaa3b
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: c7a9df15948ddea5fe76efa1cce688f704cbe5c9
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065371"
---
# <a name="incompatible-database-engine-server-collation-upgrade-advisor"></a>Inkompatible Serversortierung für Datenbank-Engine (Upgrade Advisor)
  Der Upgrade Advisor hat erkannt, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dass eine Instanz von verwendet [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , die für die Verwendung einer nicht kompatiblen Server Sortierung konfiguriert ist.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Im SharePoint-Modus.|  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>BESCHREIBUNG  
 Der Upgrade Advisor hat erkannt, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dass eine Instanz von verwendet [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , die für die Verwendung einer nicht kompatiblen Server Sortierung konfiguriert ist.  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Der SharePoint-Modus nutzt die SharePoint-Architektur für gemeinsame Dienste. SharePoint unterstützt für Groß-/Kleinschreibung beachtende oder Serversortierungen oder binäre Serversortierungen konfigurierten [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] nicht. Nicht kompatible Sortierungen schließen Sortierungen sein, bei denen standardmäßig zwischen Groß-/Kleinschreibung unterschieden wird bzw. die eine binäre Sortierung aufweisen, und eine Basissortierung, die standardmäßig kompatibel ist, aber anhand eines der folgenden Sortierungskennzeichner konfiguriert wurde:  
  
-   **Binär (Binary)**  
  
-   **Groß-/Kleinschreibung**  
  
-   **Binär-Codepunkt**  
  
 Da die aktuelle [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]-Serversortierung nicht kompatibel ist, werden Upgrades blockiert.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Die [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]-Eigenschaft für die Serversortierung kann nicht geändert werden. Sie sind nicht in der Lage, ein Upgrade von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] abzuschließen. Sie müssen die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Installation zu einem neuen Server migrieren, der eine kompatible Serversortierung verwendet. Weitere Informationen finden Sie unter  
  
-   [Aktualisieren und Migrieren von Reporting Services](https://go.microsoft.com/fwlink/?LinkId=233227)  
  
-   [Auswählen einer SQL Server-Sortierung](https://go.microsoft.com/fwlink/?LinkId=233226)  
  
  
