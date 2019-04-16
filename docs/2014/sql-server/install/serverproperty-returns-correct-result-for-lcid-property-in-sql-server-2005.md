---
title: SERVERPROPERTY gibt korrektes Ergebnis für die LCID-Eigenschaft in SQL Server 2005 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- SERVERPROPERTY function
ms.assetid: 833a2fc9-b480-4697-aa7b-9677e78ee0b4
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3b85b15ec20579cb748cf3e09c0cded8b9e43fd9
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2019
ms.locfileid: "59582216"
---
# <a name="serverproperty-returns-correct-result-for-lcid-property-in-sql-server-2005"></a>SERVERPROPERTY gibt korrektes Ergebnis für die LCID-Eigenschaft in SQL Server 2005 zurück
  Wenn SERVERPROPERTY('LCID') für Server mit binärer Sortierung ausgeführt wird, gibt die Funktion den Windows-Gebietsschemabezeichner (LCID) zurück, der der Sortierung des Servers entspricht.  
  
> [!NOTE]  
>  Bei Batch- oder Ablaufverfolgungsdateien, die Verweise auf SERVERPROPERTY ('LCID') enthalten und auf anderen Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt werden, erkennt der Upgrade Advisor diese Verhaltensänderung nur dann, wenn die anderen Instanzen über dieselbe Sortierung verfügen wie die aktuelle Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Ändern Sie Anwendungen so, dass sie die Rückgabe des Windows-LCID, der der Sortierung des Servers entspricht, durch SERVERPROPERTY('LCID') erwarten.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
