---
title: Angeben eines Breakpointfilters
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoint filter
ms.assetid: 7bf1dddd-7b0b-4c47-8a7b-28a5569b4fa5
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 42e068120e3eae54580d58e0f4d525ab5451d864
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82703726"
---
# <a name="specify-a-breakpoint-filter"></a>Angeben eines Breakpointfilters
  Bei Verwendung eines Breakpointfilters wird ein Breakpoint nur auf angegebene Computer, Betriebssystemprozesse und Threads angewendet. Breakpointfilter werden meist beim Debuggen paralleler Anwendungen verwendet.  
  
##  <a name="filter-considerations"></a><a name="BKMK_ActionConsiderations"></a> Filteraspekte  
 Breakpointfilter werden selten mit dem [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debugger verwendet, da es sich bei [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skripts und gespeicherte Prozeduren nicht um parallele Anwendungen handelt.  
  
#### <a name="to-specify-a-breakpoint-filter"></a>So geben Sie einen Breakpointfilter an  
  
1.  Klicken Sie im Editor-Fenster mit der rechten Maustaste auf das Breakpointsymbol, und klicken Sie dann im Kontextmenü auf **Filter** .  
  
     Oder  
  
     Klicken Sie im Fenster **Breakpoint** mit der rechten Maustaste auf das Breakpointsymbol, und klicken Sie dann im Kontextmenü auf **Filter** .  
  
2.  Geben Sie im Dialogfeld **Haltepunktfilter** im Feld **Filter** Computer mit Namen oder Betriebssystemprozesse und Threads mit Namen oder ID-Nummer an:  
  
    -   `MachineName` gibt den Computer an, auf dem die Instanz der Datenbank-Engine ausgeführt wird.  
  
    -   ph x="1" /&gt; und `ProcessName` geben den Betriebssystemprozess an, von dem die Instanz der Datenbank-Engine ausgeführt wird.  
  
    -   `ThreadID` und `ThreadName` geben den Betriebssystemthread an, unter dem der Batch, die Prozedur oder die Funktion von [!INCLUDE[tsql](../../includes/tsql-md.md)] in der Instanz der Datenbank-Engine ausgeführt wird.  
  
3.  Klicken Sie auf **OK** , um die Änderungen zu implementieren, oder auf **Abbrechen** , um den Vorgang zu beenden, ohne die Änderungen zu übernehmen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Angeben einer Breakpointbedingung](specify-a-breakpoint-condition.md)   
 [Angeben einer Trefferanzahl](specify-a-hit-count.md)   
 [Angeben einer Breakpointaktion](specify-a-breakpoint-action.md)  
