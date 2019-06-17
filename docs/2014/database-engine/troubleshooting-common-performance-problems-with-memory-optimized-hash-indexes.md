---
title: Problembehandlung für häufige Leistungsprobleme bei speicheroptimierten Hashindizes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 1954a997-7585-4713-81fd-76d429b8d095
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d7ed4098feb8bfd2d156e3de2f81fbf7329915aa
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62842535"
---
# <a name="troubleshooting-common-performance-problems-with-memory-optimized-hash-indexes"></a>Problembehandlung für häufige Leistungsprobleme bei speicheroptimierten Hashindizes
  Der Schwerpunkt dieses Themas liegt auf der Problembehandlung und dem Umgehen von häufigen Problemen mit Hashindizes.  
  
## <a name="search-requires-a-subset-of-hash-index-key-columns"></a>Suche erfordert eine Teilmenge von Hashindex-Schlüsselspalten  
 **Problem:** Hash-Indizes werden Werte für alle Indexschlüsselspalten erforderlich, um den Hashwert zu berechnen, und die entsprechenden Zeilen in der Hashtabelle suchen. Wenn eine Abfrage nur Gleichheitsprädikate für eine Teilmenge der Indexschlüssel in der WHERE-Klausel enthält, kann [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] daher nicht mithilfe einer Indexsuche die Zeilen suchen, die den Prädikaten in der WHERE-Klausel entsprechen.  
  
 Im Gegensatz dazu unterstützen geordnete Indizes wie datenträgerbasierte nicht gruppierte Indizes und speicheroptimierte nicht gruppierte Indizes die Indexsuche mit einer Teilmenge der Indexschlüsselspalten, sofern es sich um die führenden Spalten im Index handelt.  
  
 **Symptom:** Dies führt zu einer leistungsverringerung, da [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] muss vollständige Tabellenscans anstelle einer Indexsuche ausführen, die in der Regel schneller ist.  
  
 **So beheben Sie:** Neben der leistungsverringerung zeigt die Überprüfung der Abfragepläne einen Scan anstelle einer Indexsuche. Bei einer relativ einfachen Abfrage zeigt die Überprüfung des Abfragetexts und der Indexdefinition auch, ob für die Suche eine Teilmenge der Indexschlüsselspalten erforderlich ist.  
  
 Betrachten Sie die folgende Tabelle und Abfrage:  
  
```sql  
CREATE TABLE [dbo].[od]  
(  
     o_id INT NOT NULL,  
     od_id INT NOT NULL,  
     p_id INT NOT NULL,  
     CONSTRAINT PK_od PRIMARY KEY NONCLUSTERED HASH (o_id, od_id) WITH (BUCKET_COUNT = 10000)  
)  
WITH (MEMORY_OPTIMIZED = ON)  
  
 SELECT p_id  
 FROM dbo.od  
 WHERE o_id=1  
```  
  
 Die Tabelle verfügt über einen Hashindex für die beiden Spalten (o_id, od_id), während die Abfrage ein Gleichheitsprädikat für (o_id) enthält. Da die Abfrage nur Gleichheitsprädikate für eine Teilmenge der Indexschlüsselspalten enthält, kann [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] keinen Indexsuchvorgang mit "PK_od" ausführen. Stattdessen muss [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auf einen vollständigen Indexscan zurückgreifen.  
  
 **Problemumgehungen:** Es gibt eine Reihe von möglichen problemumgehungen. Zum Beispiel:  
  
-   Erstellen Sie den Index mit dem Typ eines nicht gruppierten Indexes anstelle eines nicht gruppierten Hash erneut. Der speicheroptimierte nicht gruppierte Index wird sortiert, und somit kann [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] eine Indexsuche der führenden Indexschlüsselspalten ausführen. Die resultierende Primärschlüsseldefinition für das Beispiel lautet `constraint PK_od primary key nonclustered`.  
  
-   Ändern Sie den aktuellen Indexschlüssel, sodass er den Spalten in der WHERE-Klausel entspricht.  
  
-   Fügen Sie einen neuen Hashindex hinzu, der den Spalten in der WHERE-Klausel der Abfrage entspricht. Im Beispiel würde dies zu folgender Tabellendefinition führen:  
  
    ```sql  
    CREATE TABLE dbo.od  
     ( o_id INT NOT NULL,  
     od_id INT NOT NULL,  
     p_id INT NOT NULL,  
  
     CONSTRAINT PK_od PRIMARY KEY   
     NONCLUSTERED HASH (o_id,od_id) WITH (BUCKET_COUNT=10000),  
  
     INDEX ix_o_id NONCLUSTERED HASH (o_id) WITH (BUCKET_COUNT=10000)  
  
     ) WITH (MEMORY_OPTIMIZED=ON)  
    ```  
  
 Beachten Sie, dass ein speicheroptimierter Hashindex nicht einwandfrei funktioniert, wenn viele doppelte Zeilen für einen angegebenen Indexschlüsselwert vorhanden sind: Wenn im Beispiel die Anzahl der eindeutigen Werte für die Spalte "o_id" erheblich kleiner als die Anzahl der Zeilen in der Tabelle ist, wäre es nicht optimal, einen Index für (o_id) hinzuzufügen. Die bessere Lösung würde darin bestehen, den Typ des Indexes "PK_od" von Hash zu nicht gruppiert zu ändern. Weitere Informationen finden Sie unter [Determining the Correct Bucket Count for Hash Indexes](../relational-databases/indexes/indexes.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Indizes für speicheroptimierte Tabellen](../relational-databases/in-memory-oltp/memory-optimized-tables.md)  
  
  
