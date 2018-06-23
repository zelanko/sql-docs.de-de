---
title: SERVERPROPERTY gibt korrektes Ergebnis für die LCID-Eigenschaft in SQL Server 2005 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SERVERPROPERTY function
ms.assetid: 833a2fc9-b480-4697-aa7b-9677e78ee0b4
caps.latest.revision: 17
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2b0179ebe39b56082bc51cfe944e6de28e0b4a2c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36151504"
---
# <a name="serverproperty-returns-correct-result-for-lcid-property-in-sql-server-2005"></a>SERVERPROPERTY gibt korrektes Ergebnis für die LCID-Eigenschaft in SQL Server 2005 zurück
  Wenn SERVERPROPERTY('LCID') für Server mit binärer Sortierung ausgeführt wird, gibt die Funktion den Windows-Gebietsschemabezeichner (LCID) zurück, der der Sortierung des Servers entspricht.  
  
> [!NOTE]  
>  Bei Batch- oder Ablaufverfolgungsdateien, die Verweise auf SERVERPROPERTY ('LCID') enthalten und auf anderen Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt werden, erkennt der Upgrade Advisor diese Verhaltensänderung nur dann, wenn die anderen Instanzen über dieselbe Sortierung verfügen wie die aktuelle Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Ändern Sie Anwendungen so, dass sie die Rückgabe des Windows-LCID, der der Sortierung des Servers entspricht, durch SERVERPROPERTY('LCID') erwarten.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
