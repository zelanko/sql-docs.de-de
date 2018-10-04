---
title: Direktes Navigieren zum Berichtsserver (Upgrade Advisor) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 3d2814a4-318a-45ed-b093-1e852fab561f
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: af75f05708c6975a845b6077edef8109db6e5b10
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48128480"
---
# <a name="direct-browsing-to-report-server-upgrade-advisor"></a>Direktes Navigieren zum Berichtsserver (Upgrade Advisor)
  Upgrade Advisor hat erkannt, die aktuelle Installation von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ist das direkte Navigieren zum virtuellen Verzeichnis Berichtsservers.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint-Modus.|  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 Upgrade Advisor hat erkannt, die aktuelle Installation von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ist das direkte Navigieren zum virtuellen berichtsserververzeichnisses, z. B. **http://\<Servername > / ReportServer**. Dies wird in aktuellen Versionen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nicht unterstützt.  
  
> [!NOTE]  
>  Diese Regel stellt eine Warnung dar. Das Upgrade wird nicht blockiert.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Navigieren Sie mithilfe der SharePoint-Benutzeroberfläche für Dokumentbibliotheken, oder verwenden Sie **http://\<Servername > / Sharepoint-Website >/_vti_bin/Reportserver**.  
  
  
