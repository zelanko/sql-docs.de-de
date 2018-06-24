---
title: Neue Spalte in der Ausgabe von "sp_helptrigger" kann sich auf Anwendungen auswirken | Microsoft Docs
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
- sp_helptrigger
ms.assetid: b7c42a8f-f2e0-4fa3-b046-3cf39c854c47
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2d62b9b9546fa113557bf962d68876d8c55a71ef
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050693"
---
# <a name="new-column-in-output-of-sphelptrigger-may-impact-applications"></a>Neue Spalte in der Ausgabe von 'sp_helptrigger' kann möglicherweise Auswirkungen auf Anwendungen haben
  Prozedur enthält Trigger_schemaias, die vom System "sp_helptrigger" die letzte Spalte im Resultset zurückgegeben.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Um Informationen über Trigger zu erhalten, die für eine bestimmte Tabelle definiert wurden, starten Sie eine Abfrage der sys.triggers-Katalogsicht.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Überprüfen Sie die Verwendung von sp_helptrigger in Anwendungen. Sie müssen Ihre Anwendungen möglicherweise ändern, damit die zusätzliche Spalte hinzugefügt werden kann. Alternativ können Sie auch die sys.triggers-Katalogsicht verwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
