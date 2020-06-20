---
title: Neue Spalte in der Ausgabe von sp_helptrigger kann sich auf Anwendungen auswirken | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- sp_helptrigger
ms.assetid: b7c42a8f-f2e0-4fa3-b046-3cf39c854c47
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0b1f5e936843ed84a5c6b88e2f3685e7a4272bc2
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85012174"
---
# <a name="new-column-in-output-of-sp_helptrigger-may-impact-applications"></a>Neue Spalte in der Ausgabe von 'sp_helptrigger' kann möglicherweise Auswirkungen auf Anwendungen haben
  trigger_schemaias die letzte Spalte im Resultset zurück, das von der gespeicherten System Prozedur sp_helptrigger zurückgegeben wurde.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Um Informationen über Trigger zu erhalten, die für eine bestimmte Tabelle definiert wurden, starten Sie eine Abfrage der sys.triggers-Katalogsicht.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Überprüfen Sie die Verwendung von sp_helptrigger in Anwendungen. Sie müssen Ihre Anwendungen möglicherweise ändern, damit die zusätzliche Spalte hinzugefügt werden kann. Alternativ können Sie auch die sys.triggers-Katalogsicht verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
