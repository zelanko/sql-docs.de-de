---
title: Datenbankübergreifende Abfragen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a0305f5b-91bd-4d18-a2fc-ec235b062fd3
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4a05172ba60d8aa200191065663f931a6bbffc03
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37264756"
---
# <a name="cross-database-queries"></a>Datenbankübergreifende Abfragen
  In [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]bieten speicheroptimierte Tabellen keine Unterstützung für datenbankübergreifende Transaktionen. Innerhalb einer Transaktion oder Abfrage, die auf eine speicheroptimierte Tabelle zugreift, können Sie nicht gleichzeitig auf eine andere Datenbank zugreifen. Daten aus einer Tabelle in einer Datenbank können nicht einfach in eine speicheroptimierte Tabelle in einer anderen Datenbank kopiert werden.  
  
 Tabellenvariablen sind nicht transaktional. Daher können speicheroptimierte Tabellenvariablen in datenbankübergreifenden Abfragen verwendet werden, um Daten aus einer Datenbank in speicheroptimierte Tabellen in einer anderen Datenbank zu verschieben. Sie können zwei Transaktionen verwenden. In der ersten Transaktion fügen Sie die Daten aus der Remotetabelle in die Variable ein. In der zweiten Transaktion fügen Sie die Daten aus der Variablen in die lokale speicheroptimierte Tabelle ein.  
  
 Beispielsweise, um die Zeile aus Tabelle t1 in Datenbank db1 in Tabelle t2 in db2 mit Variablen kopieren @v1 des Typs dbo. tt1 können etwa so:  
  
```tsql  
USE db2   
GO   
DECLARE @v1 dbo.tt1   
INSERT @v1 SELECT * FROM db1.dbo.t1   
INSERT dbo.t2 SELECT * FROM @v1   
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Migrieren zu In-Memory OLTP](migrating-to-in-memory-oltp.md)  
  
  
