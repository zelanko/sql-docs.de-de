---
title: Direktes Navigieren zum Berichtsserver (Upgrade Advisor) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 3d2814a4-318a-45ed-b093-1e852fab561f
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 870937f4dffe356ca2216335c74566efc73d2a52
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66095538"
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
  
  
