---
title: Ungültiger Named Pipe Name kann das Upgrade blockieren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- invalid named pipes [SQL Server]
- named pipes
ms.assetid: 58c2199c-4fdf-4d43-ac1c-842703344b75
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: bacfd3d097d7cccb0a5780328c4db95dc5afc733
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059244"
---
# <a name="invalid-named-pipe-name-can-block-upgrade"></a>Ungültiger Named Pipe-Name kann Upgrade blockieren
  Das Upgrade schlägt fehl, wenn das Named Pipes-Protokoll falsch konfiguriert ist.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>BESCHREIBUNG  
 Während des Upgrades startet das Setup Programm die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] Instanz mit Shared Memory-Unterstützung, einer Named Pipe, die nur lokale Verbindungen akzeptiert. Wenn der auf dem Server angegebene Pipename nicht leer ist, muss er mit der Zeichenfolge " \\ \\ .\pipe" beginnen, \\ um gültig zu sein. Wenn der Named Pipe-Name nicht gültig ist, startet [!INCLUDE[ssDE](../../includes/ssde-md.md)] nicht, und das Setup schlägt fehl.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Verwenden Sie das ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Netzwerk Hilfsprogramm** , um einen gültigen Pipenamen anzugeben, und führen Sie dann das Setup aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
