---
title: Microsoft SQL Server Reporting Services SharePoint Shared Service wird installiert parallel (Upgrade Advisor) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 6ae1017e-129b-4702-9ea7-00ac9b024062
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 93bbc8ca6c2a67ec2ec224db51c780a38534c098
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48162510"
---
# <a name="microsoft-sql-server-reporting-services-sharepoint-shared-service-is-installed-side-by-side-upgrade-advisor"></a>Gemeinsamer SharePoint-Dienst für Microsoft SQL Server Reporting Services wird parallel installiert (Upgrade Advisor)
  Upgrade Advisor hat erkannt [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] gemeinsamer SharePoint-Dienst wird parallel zu einer früheren Version von installiert [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint-Modus.|  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 Upgrade Advisor hat erkannt [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] freigegebenen SharePoint-Dienst wird parallel zu einer früheren Version von installiert [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , die nicht in der gemeinsame SharePoint-Dienstarchitektur basiert. Da sowohl die ältere als auch die neuere [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-SharePoint-Technologie parallel auf dem Computer installiert sind, wird das Upgrade blockiert.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Um das Upgrade fortzusetzen, muss eine der vorhandenen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Installationen deinstalliert werden. Nachdem Sie eine der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Installationen entfernt haben, führen Sie den Upgrade Advisor erneut aus, um zu überprüfen, ob weitere Upgradeprobleme vorliegen.  
  
  
