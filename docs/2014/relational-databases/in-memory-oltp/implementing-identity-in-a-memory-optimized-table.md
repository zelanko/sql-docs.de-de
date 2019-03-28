---
title: Implementieren von IDENTITY in einer speicheroptimierten Tabelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c0a704a3-3a31-4c2c-b967-addacda62ef8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 591d86011ee769d054c069db98a40e2765b1ec27
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58538132"
---
# <a name="implementing-identity-in-a-memory-optimized-table"></a>Implementieren von IDENTITY in einer speicheroptimierten Tabelle
  IDENTITY(1, 1) wird in einer speicheroptimierten Tabelle unterstützt. Identitätsspalten mit der Definition IDENTITY(x, y), wobei x != 1 oder y != 1 ist, werden in speicheroptimierten Tabellen jedoch nicht unterstützt. Die problemumgehung für IDENTITY-Werte verwendet, das Sequenzobjekt ([Sequenznummern](../sequence-numbers/sequence-numbers.md)).  
  
 Entfernen Sie zuerst die IDENTITY-Eigenschaft aus der Tabelle, die in In-Memory OLTP konvertiert wird. Definieren Sie anschließend ein neues SEQUENCE-Objekt für die Spalte in der Tabelle. SEQUENCE-Objekte als Identitätsspalten stützen sich auf die Möglichkeit, DEFAULT-Werte für Spalten zu erstellen, die mithilfe der NEXT VALUE FOR-Syntax einen neuen Identitätswert abrufen. Da DEFAULT-Werte von In-Memory OLTP nicht unterstützt werden, müssen Sie den neu generierten SEQUENCE-Wert entweder an die INSERT-Anweisung oder an eine systemintern kompilierte gespeicherte Prozedur übergeben, die den Einfügevorgang ausführt. Dieses Muster wird im folgenden Beispiel veranschaulicht.  
  
```sql  
-- Create a new In-Memory OLTP table to simulate IDENTITY insert  
-- Here the column C1 was the identity column in the original table  
--  
create table T1  
(  
  
[c1] integer not null primary key T1_c1 nonclustered,  
[c2] varchar(32) not null,  
[c3] datetime not null  
  
) with (memory_optimized = on)  
go  
  
-- This is a sequence provider that will give us values for column [c1]  
--  
create sequence usq_SequenceForT1 as integer start with 2 increment by 1  
go  
  
--   insert a sample row using the sequence  
--   note that a new value needs to be retrieved form   
--   the sequence object for every insert  
--  
declare @c1 integer = next value for [dbo].[usq_SequenceForT1]  
insert into T1 values (@c1, 'test', getdate())  
```  
  
 Nachdem Sie den Einfügevorgang mehrmals ausgeführt haben, stellen Sie fest, dass in Spalte [c1] monoton steigende Werte enthalten sind. Dieses Resultset wird mit dem Tabellenscan und dem Hashindex ohne `ORDER BY` generiert, sodass die Zeilen nicht sortiert sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Migrieren zu In-Memory OLTP](migrating-to-in-memory-oltp.md)  
  
  
