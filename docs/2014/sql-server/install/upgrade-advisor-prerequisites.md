---
title: Upgrade Advisor-Voraussetzungen | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 60
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7fb8f505610607052c12c68e910185a2a5e48f16
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150503"
---
# <a name="upgrade-advisor-prerequisites"></a>Voraussetzungen für den Upgrade Advisor
  In diesem Thema werden die Softwareanforderungen für den Upgrade Advisor beschrieben.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Installieren und Ausführen des Upgrade Advisors müssen folgende Voraussetzungen erfüllt sein:  
  
-   [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] SP1, [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] beginnend mit SP2, Windows 7 oder [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] R2.  
  
-   Windows Installer 4.5. Sie können Windows Installer von der [Windows Installer-Website](http://go.microsoft.com/fwlink/?LinkId=49112).  
  
-   Der [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], beginnend mit .NET Framework 4. Die [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] steht auf der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Produktmedien, und von der [SDKS, Redistributables und Servicepack-Downloadwebsite](http://go.microsoft.com/fwlink/?LinkId=48882).  
  
    -   Um .NET Framework 4 von den [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Medien zu installieren, suchen Sie das Stammverzeichnis des Datenträgerlaufwerks. Doppelklicken Sie dann auf den Ordner \redist und auf den Ordner DotNetFrameworks und führen Sie dotNetFx40_Full_x86_x64.exe aus (für 32-Bit- und 64-Bit-Betriebssysteme).  
  
-   Die [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom ist eine Voraussetzung für die Installation von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor und wird vom Setup für Upgrade Advisor nicht installiert. Das Setup erfordert, dass Sie zum Herunterladen und Installieren der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom aus dem [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Feature Pack.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Installieren des Upgrade Advisors](../../../2014/sql-server/install/how-to-install-upgrade-advisor.md)  
  
  