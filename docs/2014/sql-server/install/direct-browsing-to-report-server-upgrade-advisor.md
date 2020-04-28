---
title: Direktes Navigieren zum Berichts Server (Upgrade Advisor) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 3d2814a4-318a-45ed-b093-1e852fab561f
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 6945828b2eba829c32d717c13393c9fbda4fc43e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "71952210"
---
# <a name="direct-browsing-to-report-server-upgrade-advisor"></a>Direktes Navigieren zum Berichtsserver (Upgrade Advisor)
  Der Upgrade Advisor hat festgestellt, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dass Ihre aktuelle Installation von direkt zum virtuellen Verzeichnis des Berichts Servers durchsucht.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Im SharePoint-Modus.|  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>BESCHREIBUNG  
 Der Upgrade Advisor hat festgestellt, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dass Ihre aktuelle Installation von direkt zum virtuellen Verzeichnis des Berichts Servers durchsucht, z. b. **http://\<Servername>/ReportServer**. Dies wird in aktuellen Versionen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nicht unterstützt.  
  
> [!NOTE]  
>  Diese Regel stellt eine Warnung dar. Das Upgrade wird nicht blockiert.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Navigieren Sie über die SharePoint-Benutzeroberfläche für Dokument Bibliotheken, oder verwenden Sie **http://\<Servername>/SharePoint Site>/_vti_bin/ReportServer**.  
  
  
