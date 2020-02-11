---
title: Hash Indizes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f4bdc9c1-7922-4fac-8183-d11ec58fec4e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 263fdcd4b09c4acc6c2bba4d67629f867d64c6b3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62779486"
---
# <a name="hash-indexes"></a>Hashindizes
  Indizes werden als Einstiegspunkte für speicheroptimierte Tabellen verwendet. Das Lesen von Zeilen aus einer Tabelle erfordert einen Index, um Daten im Arbeitsspeicher zu suchen.  
  
 Ein Hashindex besteht aus einer Sammlung von Buckets, die in einem Array organisiert sind. Eine Hashfunktion ordnet Indexschlüssel den entsprechenden Buckets im Hashindex zu. Die folgende Abbildung zeigt drei Indexschlüssel, die drei verschiedenen Buckets im Hashindex zugeordnet sind. Zur Veranschaulichung lautet der Hashfunktionsname f(x).  
  
 ![Indexschlüssel, die unterschiedlichen Buckets zugeordnet sind.](../../2014/database-engine/media/hekaton-tables-2.gif "Indexschlüssel, die unterschiedlichen Buckets zugeordnet sind.")  
  
 Die Hashfunktion, die für Hashindizes verwendet wird, weist die folgenden Merkmale auf:  
  
-   
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] hat eine Hashfunktion, die für alle Hashindizes verwendet wird.  
  
-   Die Hashfunktion ist deterministisch. Der gleiche Indexschlüssel wird immer dem gleichen Bucket im Hashindex zugeordnet.  
  
-   Mehrere Indexschlüssel können dem gleichen Hashbucket zugeordnet werden.  
  
-   Die Hashfunktion ist ausgeglichen. Dies bedeutet, dass die Verteilung der Indexschlüsselwerte auf Hashbuckets üblicherweise einer Poisson-Verteilung entspricht.  
  
     Eine Poisson-Verteilung ist keine gleichmäßige Verteilung. Indexschlüsselwerte werden in die Hashbuckets nicht gleichmäßig verteilt. So führt beispielsweise eine Poisson-Verteilung von *n* unterschiedlichen Indexschlüsseln auf *n* Hashbuckets dazu, dass ungefähr ein Drittel der Buckets leer ist, ein Drittel der Buckets einen Indexschlüssel enthält und das letzte Drittel der Buckets zwei Indexschlüssel enthält. Eine kleine Anzahl von Buckets enthält mehr als zwei Schlüssel.  
  
 Wenn zwei Indexschlüssel dem gleichen Hashbucket zugeordnet werden, gibt es einen Hashkonflikt. Eine große Anzahl von Hashkonflikten kann sich auf die Leistung bei Lesevorgängen auswirken.  
  
 Die Hashindexstruktur im Arbeitsspeicher besteht aus einem Array von Speicherzeigern. Jedes Bucket ist einem Offset in diesem Array zugeordnet. Jeder Bucket im Array zeigt auf die erste Zeile in diesem Hashbucket. Jede Zeile im Bucket zeigt auf die nächste Zeile, was eine Kette von Zeilen für jeden Hashbucket ergibt, wie in der folgenden Abbildung veranschaulicht.  
  
 ![Die Hashindexstruktur im Arbeitsspeicher.](../../2014/database-engine/media/hekaton-tables-3.gif "Die Hashindexstruktur im Arbeitsspeicher.")  
  
 Die Abbildung weist drei Buckets mit Zeilen auf. Der zweite Bucket von oben enthält die drei roten Zeilen. Der vierte Bucket enthält die einzelne blaue Zeile. Der untere Bucket enthält die zwei grünen Zeilen. Diese können unterschiedliche Versionen derselben Zeile sein.  
  
 Weitere Informationen zu Indizes für speicheroptimierte Tabellen finden Sie unter [Guidelines for Using Indexes on Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Indizes für speicheroptimierte Tabellen](../../2014/database-engine/indexes-on-memory-optimized-tables.md)  
  
  
