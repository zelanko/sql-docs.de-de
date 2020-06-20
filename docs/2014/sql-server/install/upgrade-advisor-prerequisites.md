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
ms.openlocfilehash: 41c97cf585d1768c7aebeec2613ee8744cb220da
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85062355"
---
# <a name="upgrade-advisor-prerequisites"></a>Voraussetzungen für den Upgrade Advisor
  In diesem Thema werden die Softwareanforderungen für den Upgrade Advisor beschrieben.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Zum Installieren und Ausführen des Upgrade Advisors müssen folgende Voraussetzungen erfüllt sein:  
  
-   [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] SP1, [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] beginnend mit SP2, Windows 7 oder [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] R2.  
  
-   Windows Installer 4.5. Sie können Windows Installer von der [Windows Installer Website](https://www.microsoft.com/download/details.aspx?id=8483)installieren.  
  
-   Der [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], beginnend mit .NET Framework 4. Der [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ist auf dem [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Produkt Medium und auf der Website des [SDK, der weitervertreibbaren Website und der Service Pack Download-](https://go.microsoft.com/fwlink/?LinkId=48882)Website verfügbar.  
  
    -   Um .NET Framework 4 von den [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Medien zu installieren, suchen Sie das Stammverzeichnis des Datenträgerlaufwerks. Doppelklicken Sie dann auf den Ordner \redist und auf den Ordner DotNetFrameworks und führen Sie dotNetFx40_Full_x86_x64.exe aus (für 32-Bit- und 64-Bit-Betriebssysteme).  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom ist eine Voraussetzung für die Installation [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] von Upgrade Advisor und wird vom Upgrade Advisor-Setup nicht installiert. Das Setup erfordert, dass Sie das [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom aus dem [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Feature Pack herunterladen und installieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gewusst wie: Installieren des Upgrade Advisors](../../../2014/sql-server/install/how-to-install-upgrade-advisor.md)  
  
  
