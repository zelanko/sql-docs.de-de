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
manager: craigg
ms.openlocfilehash: fbd4c1e55bb49c6ae8f75d3d12cc243df963018a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "71952235"
---
# <a name="incompatible-database-engine-server-collation-upgrade-advisor"></a>Inkompatible Serversortierung für Datenbank-Engine (Upgrade Advisor)
  Der Upgrade Advisor [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] hat erkannt, dass eine Instanz [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] von verwendet, die für die Verwendung einer nicht kompatiblen Server Sortierung konfiguriert ist.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Im SharePoint-Modus.|  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>BESCHREIBUNG  
 Der Upgrade Advisor [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] hat erkannt, dass eine Instanz [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] von verwendet, die für die Verwendung einer nicht kompatiblen Server Sortierung konfiguriert ist.  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Der SharePoint-Modus nutzt die SharePoint-Architektur für gemeinsame Dienste. SharePoint unterstützt für Groß-/Kleinschreibung beachtende oder Serversortierungen oder binäre Serversortierungen konfigurierten [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] nicht. Nicht kompatible Sortierungen schließen Sortierungen sein, bei denen standardmäßig zwischen Groß-/Kleinschreibung unterschieden wird bzw. die eine binäre Sortierung aufweisen, und eine Basissortierung, die standardmäßig kompatibel ist, aber anhand eines der folgenden Sortierungskennzeichner konfiguriert wurde:  
  
-   **Ärer**  
  
-   **Groß-/Kleinschreibung**  
  
-   **Binär-Codepunkt**  
  
 Da die aktuelle [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]-Serversortierung nicht kompatibel ist, werden Upgrades blockiert.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Die [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]-Eigenschaft für die Serversortierung kann nicht geändert werden. Sie sind nicht in der Lage, ein Upgrade von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] abzuschließen. Sie müssen die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Installation zu einem neuen Server migrieren, der eine kompatible Serversortierung verwendet. Weitere Informationen finden Sie unter  
  
-   [Aktualisieren und Migrieren von Reporting Services](https://go.microsoft.com/fwlink/?LinkId=233227)  
  
-   [Auswählen einer SQL Server-Sortierung](https://go.microsoft.com/fwlink/?LinkId=233226)  
  
  
