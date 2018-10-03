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
ms.openlocfilehash: d800001d2bf5ec663ad2c3651aae59baccca445b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48057850"
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
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
