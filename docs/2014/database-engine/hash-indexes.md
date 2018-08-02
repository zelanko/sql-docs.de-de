---
title: Hashindizes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f4bdc9c1-7922-4fac-8183-d11ec58fec4e
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f2c2b4c055eea6aef2e7825ee6589c6611ceaf7a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37295230"
---
# <a name="hash-indexes"></a>Hashindizes
  Indizes werden als Einstiegspunkte für speicheroptimierte Tabellen verwendet. Das Lesen von Zeilen aus einer Tabelle erfordert einen Index, um Daten im Arbeitsspeicher zu suchen.  
  
 Ein Hashindex besteht aus einer Sammlung von Buckets, die in einem Array organisiert sind. Eine Hashfunktion ordnet Indexschlüssel den entsprechenden Buckets im Hashindex zu. Die folgende Abbildung zeigt drei Indexschlüssel, die drei verschiedenen Buckets im Hashindex zugeordnet sind. Zur Veranschaulichung lautet der Hashfunktionsname f(x).  
  
 ![Der Indexschlüssel, die verschiedenen Buckets zugeordnet. ] (../../2014/database-engine/media/hekaton-tables-2.gif "Indexschlüssel, die verschiedenen Buckets zugeordnet.")  
  
 Die Hashfunktion, die für Hashindizes verwendet wird, weist die folgenden Merkmale auf:  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] hat eine Hashfunktion, die für alle Hashindizes verwendet wird.  
  
-   Die Hashfunktion ist deterministisch. Der gleiche Indexschlüssel wird immer dem gleichen Bucket im Hashindex zugeordnet.  
  
-   Mehrere Indexschlüssel können dem gleichen Hashbucket zugeordnet werden.  
  
-   Die Hashfunktion ist ausgeglichen. Dies bedeutet, dass die Verteilung der Indexschlüsselwerte auf Hashbuckets üblicherweise einer Poisson-Verteilung entspricht.  
  
     Eine Poisson-Verteilung ist keine gleichmäßige Verteilung. Indexschlüsselwerte werden in die Hashbuckets nicht gleichmäßig verteilt. So führt beispielsweise eine Poisson-Verteilung von *n* unterschiedlichen Indexschlüsseln auf *n* Hashbuckets dazu, dass ungefähr ein Drittel der Buckets leer ist, ein Drittel der Buckets einen Indexschlüssel enthält und das letzte Drittel der Buckets zwei Indexschlüssel enthält. Eine kleine Anzahl von Buckets enthält mehr als zwei Schlüssel.  
  
 Wenn zwei Indexschlüssel dem gleichen Hashbucket zugeordnet werden, gibt es einen Hashkonflikt. Eine große Anzahl von Hashkonflikten kann sich auf die Leistung bei Lesevorgängen auswirken.  
  
 Die Hashindexstruktur im Arbeitsspeicher besteht aus einem Array von Speicherzeigern. Jedes Bucket ist einem Offset in diesem Array zugeordnet. Jeder Bucket im Array zeigt auf die erste Zeile in diesem Hashbucket. Jede Zeile im Bucket zeigt auf die nächste Zeile, was eine Kette von Zeilen für jeden Hashbucket ergibt, wie in der folgenden Abbildung veranschaulicht.  
  
 ![Die Struktur des in-Memory-Hash-Index. ] (../../2014/database-engine/media/hekaton-tables-3.gif "Die hashindexstruktur im Arbeitsspeicher.")  
  
 Die Abbildung weist drei Buckets mit Zeilen auf. Der zweite Bucket von oben enthält die drei roten Zeilen. Der vierte Bucket enthält die einzelne blaue Zeile. Der untere Bucket enthält die zwei grünen Zeilen. Diese können unterschiedliche Versionen derselben Zeile sein.  
  
 Weitere Informationen zu Indizes für Speicheroptimierte Tabellen finden Sie unter [Richtlinien zum Verwenden von Indizes für Speicheroptimierte Tabellen](../relational-databases/in-memory-oltp/memory-optimized-tables.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Indizes für speicheroptimierte Tabellen](../../2014/database-engine/indexes-on-memory-optimized-tables.md)  
  
  
