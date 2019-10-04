---
title: Microsoft SQL Server Reporting Services gemeinsamer gemeinsamer SharePoint-Dienst parallel (Upgrade Advisor) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 6ae1017e-129b-4702-9ea7-00ac9b024062
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 529e07dc7beed8dc37741f6c9dab0b0b080d4898
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952696"
---
# <a name="microsoft-sql-server-reporting-services-sharepoint-shared-service-is-installed-side-by-side-upgrade-advisor"></a>Gemeinsamer SharePoint-Dienst für Microsoft SQL Server Reporting Services wird parallel installiert (Upgrade Advisor)
  Der Upgrade Advisor hat erkannt [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] der gemeinsame SharePoint-Dienst wird parallel zu einer früheren Version von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installiert.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus.|  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Beschreibung  
 Der Upgrade Advisor hat erkannt, dass [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] der gemeinsame SharePoint-Dienst parallel mit einer früheren Version von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installiert ist, die nicht auf der Architektur des gemeinsamen SharePoint-diensdienstanbieter basiert. Da sowohl die ältere als auch die neuere [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-SharePoint-Technologie parallel auf dem Computer installiert sind, wird das Upgrade blockiert.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Um das Upgrade fortzusetzen, muss eine der vorhandenen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Installationen deinstalliert werden. Nachdem Sie eine der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Installationen entfernt haben, führen Sie den Upgrade Advisor erneut aus, um zu überprüfen, ob weitere Upgradeprobleme vorliegen.  
  
  
