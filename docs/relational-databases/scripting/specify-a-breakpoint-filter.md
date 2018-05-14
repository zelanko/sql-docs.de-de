---
title: Angeben eines Breakpointfilters | Microsoft Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology:
- database-engine
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vs.debug.breakpt.contraints
helpviewer_keywords:
- Transact-SQL debugger, breakpoint filter
ms.assetid: 7bf1dddd-7b0b-4c47-8a7b-28a5569b4fa5
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 0748a0d35c4fd57f8b0834d968ee5b3164524f49
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="specify-a-breakpoint-filter"></a>Angeben eines Breakpointfilters
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Bei Verwendung eines Breakpointfilters wird ein Breakpoint nur auf angegebene Computer, Betriebssystemprozesse und Threads angewendet. Breakpointfilter werden meist beim Debuggen paralleler Anwendungen verwendet.  
  
##  <a name="BKMK_ActionConsiderations"></a> Filteraspekte  
 Breakpointfilter werden selten mit dem [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debugger verwendet, da es sich bei [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skripts und gespeicherte Prozeduren nicht um parallele Anwendungen handelt.  
  
#### <a name="to-specify-a-breakpoint-filter"></a>So geben Sie einen Breakpointfilter an  
  
1.  Klicken Sie im Editor-Fenster mit der rechten Maustaste auf das Breakpointsymbol, und klicken Sie dann im Kontextmenü auf **Filter** .  
  
     -oder-  
  
     Klicken Sie im Fenster **Breakpoint** mit der rechten Maustaste auf das Breakpointsymbol, und klicken Sie dann im Kontextmenü auf **Filter** .  
  
2.  Geben Sie im Dialogfeld **Haltepunktfilter** im Feld **Filter** Computer mit Namen oder Betriebssystemprozesse und Threads mit Namen oder ID-Nummer an:  
  
    -   
  **MachineName** gibt den Computer an, auf dem die Instanz der Datenbank-Engine ausgeführt wird.  
  
    -   
  **ProcessID**und **ProcessName** geben den Betriebssystemprozess an, von dem die Instanz der Datenbank-Engine ausgeführt wird.  
  
    -   
  **ThreadID** und **ThreadName** geben den Betriebssystemthread an, unter dem der Batch, die Prozedur oder die Funktion von [!INCLUDE[tsql](../../includes/tsql-md.md)] in der Instanz der Datenbank-Engine ausgeführt wird.  
  
3.  Klicken Sie auf **OK** , um die Änderungen zu implementieren, oder auf **Abbrechen** , um den Vorgang zu beenden, ohne die Änderungen zu übernehmen.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Angeben einer Breakpointbedingung](../../relational-databases/scripting/specify-a-breakpoint-condition.md)   
 [Angeben einer Trefferanzahl](../../relational-databases/scripting/specify-a-hit-count.md)   
 [Angeben einer Breakpointaktion](../../relational-databases/scripting/specify-a-breakpoint-action.md)  
  
  
