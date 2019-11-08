---
title: Voraussetzungen für den Upgrade Advisor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- requirements [Upgrade Advisor]
- software [Upgrade Advisor]
- system requirements [Upgrade Advisor]
- Setup [Upgrade Advisor]
- SQL Server Upgrade Advisor, prerequisites
- prerequisites [Upgrade Advisor]
- Upgrade Advisor [SQL Server], prerequisites
ms.assetid: d21a39e5-5f81-4096-a7dd-f244e4779992
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5875ad2268e14d6bbe276ea437c5ee201867105e
ms.sourcegitcommit: 66dbc3b740f4174f3364ba6b68bc8df1e941050f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2019
ms.locfileid: "73632773"
---
# <a name="upgrade-advisor-prerequisites"></a>Voraussetzungen für den Upgrade Advisor
  In diesem Thema werden die Softwareanforderungen für den Upgrade Advisor beschrieben.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Installieren und Ausführen des Upgrade Advisors müssen folgende Voraussetzungen erfüllt sein:  
  
-   [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] SP1, [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] beginnend mit SP2, Windows 7 oder [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] R2.  
  
-   Windows Installer 4.5. Sie können Windows Installer von der [Windows Installer Website](https://www.microsoft.com/download/details.aspx?id=8483)installieren.  
  
-   Der [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], beginnend mit .NET Framework 4. Der [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ist auf den [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Produktmedien und auf der Website des [SDK, der weitervertreibbaren Website und der Service Pack Download](https://go.microsoft.com/fwlink/?LinkId=48882)-Website verfügbar.  
  
    -   Um .NET Framework 4 von den [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Medien zu installieren, suchen Sie das Stammverzeichnis des Datenträgerlaufwerks. Doppelklicken Sie dann auf den Ordner \redist und auf den Ordner DotNetFrameworks und führen Sie dotNetFx40_Full_x86_x64.exe aus (für 32-Bit- und 64-Bit-Betriebssysteme).  
  
-   Die [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom ist eine Voraussetzung für die Installation von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor und wird nicht durch das Upgrade Advisor-Setup installiert. Das Setup erfordert, dass Sie die [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom aus dem [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Feature Pack herunterladen und installieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Installieren des Upgrade Advisors](../../../2014/sql-server/install/how-to-install-upgrade-advisor.md)  
  
  
