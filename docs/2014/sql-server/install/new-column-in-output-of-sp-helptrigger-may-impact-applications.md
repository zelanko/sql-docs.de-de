---
title: Neue Spalte in der Ausgabe von ' sp_helptrigger ' kann Auswirkungen auf Anwendungen haben | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 33d47c858a03766260e8ed8c098fef79e9e4a82f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66093737"
---
# <a name="new-column-in-output-of-sphelptrigger-may-impact-applications"></a>Neue Spalte in der Ausgabe von 'sp_helptrigger' kann möglicherweise Auswirkungen auf Anwendungen haben
  die letzte Spalte im Resultset vom System ' sp_helptrigger ' zurückgegebenen Trigger_schemaias gespeicherten Prozedur.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Um Informationen über Trigger zu erhalten, die für eine bestimmte Tabelle definiert wurden, starten Sie eine Abfrage der sys.triggers-Katalogsicht.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Überprüfen Sie die Verwendung von sp_helptrigger in Anwendungen. Sie müssen Ihre Anwendungen möglicherweise ändern, damit die zusätzliche Spalte hinzugefügt werden kann. Alternativ können Sie auch die sys.triggers-Katalogsicht verwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
