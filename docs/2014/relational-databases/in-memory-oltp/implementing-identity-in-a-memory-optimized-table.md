---
title: Implementieren von IDENTITY in einer speicheroptimierten Tabelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c0a704a3-3a31-4c2c-b967-addacda62ef8
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a3fe549e5a49dcc7c0c0417199206a6fd34079ac
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82706498"
---
# <a name="implementing-identity-in-a-memory-optimized-table"></a>Implementieren von IDENTITY in einer speicheroptimierten Tabelle
  IDENTITY(1, 1) wird in einer speicheroptimierten Tabelle unterstützt. Identitätsspalten mit der Definition IDENTITY(x, y), wobei x != 1 oder y != 1 ist, werden in speicheroptimierten Tabellen jedoch nicht unterstützt. Die Problem Umgehung für Identitäts Werte verwendet das Sequenz Objekt ([Sequenznummern](../sequence-numbers/sequence-numbers.md)).  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Migrieren zu In-Memory OLTP](migrating-to-in-memory-oltp.md)  
  
  
