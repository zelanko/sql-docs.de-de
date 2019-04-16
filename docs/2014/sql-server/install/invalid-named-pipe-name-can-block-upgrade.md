---
title: Ungültige named Pipe-Name kann Upgrade blockieren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- invalid named pipes [SQL Server]
- named pipes
ms.assetid: 58c2199c-4fdf-4d43-ac1c-842703344b75
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ad261d8d7680be7111e79a1b7a7f3291c2139308
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2019
ms.locfileid: "59582813"
---
# <a name="invalid-named-pipe-name-can-block-upgrade"></a>Ungültiger Named Pipe-Name kann Upgrade blockieren
  Das Upgrade schlägt fehl, wenn das Named Pipes-Protokoll falsch konfiguriert ist.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Während des Upgrades, startet das Setupprogramm die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz mit Unterstützung von freigegebenem Arbeitsspeicher, einer named Pipe, die nur lokale Verbindungen akzeptiert. Wenn die auf dem Server angegebene Named Pipe nicht leer ist, muss die beginnen mit der Zeichenfolge "\\\\. \pipe\\" gültig ist. Wenn der Named Pipe-Name nicht gültig ist, startet [!INCLUDE[ssDE](../../includes/ssde-md.md)] nicht, und das Setup schlägt fehl.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Verwenden der  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Netzwerkkonfiguration** auf einen gültigen Pipenamen anzugeben, und führen Sie Setup.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
