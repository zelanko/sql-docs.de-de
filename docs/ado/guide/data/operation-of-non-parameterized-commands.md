---
title: Von nicht parametrisierten Befehlen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- non-parameterized commands [ADO]
- data shaping [ADO], non-parameterized commands
ms.assetid: 9700e50a-9f17-4ba3-8afb-f750741dc6ca
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 884ef4e72b975de0eb9dd92e80ec3ce0d513546b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47822148"
---
# <a name="operation-of-non-parameterized-commands"></a>Verarbeitung nicht-parametrisierter Befehle
Für nicht parametrisierte Befehle, die alle die Anbieterbefehle ausgeführt werden und die **Recordsets** werden während der Ausführung des Befehls erstellt. Wenn der Befehl, synchron ausgeführt wird, alle der **Recordsets** wird vollständig aufgefüllt. Wenn ein asynchrone Auffüllungsmodus ausgewählt wurde, den Auffüllungsstatus der der **Recordsets** hängt von der Auffüllungsmodus und die Größe des der **Recordsets**.  
  
 Z. B. der *übergeordnete Befehl* zurückgeben könnte eine **Recordset** von Kunden für ein Unternehmen in einer Customers-Tabelle, und die *untergeordneten Befehl* konnte eine zurückgeben**Recordset** der Aufträge für alle Kunden aus einer Orders-Tabelle.  
  
```  
SHAPE {SELECT * FROM Customers}   
   APPEND ({SELECT * FROM Orders} AS chapOrders   
   RELATE customerID TO customerID)  
```  
  
 Für nicht parametrisierte über-/ unterordnungsbeziehung, jeden über- und untergeordneten **Recordset** Objekt müssen eine Spalte gemeinsam, um diese zu verknüpfen. Die Spalten werden in der RELATE-Klausel mit dem Namen *übergeordnete Spalte* erste und dann *untergeordnete Spalte*. Die Spalten möglicherweise unterschiedliche Namen aufweisen, in den jeweiligen **Recordset** Objekte, sondern muss auf die gleichen Informationen verweisen, um eine sinnvolle Beziehung angeben. Z. B. die **Kunden** und **Orders-Recordset** Objekte können sowohl eine "KundenID" aufweisen. Da die Mitgliedschaft der untergeordneten **Recordset** richtet sich nach den Anbieterbefehl aus, das untergeordnete Element **Recordset** kann verwaiste Zeilen enthalten. Diese verwaisten Zeilen werden ohne zusätzliche neu gestaltet werden, kann nicht zugegriffen.  
  
 Strukturieren von Daten eine Kapitelspalte angefügt, das dem übergeordneten **Recordset**. Die Werte in der Kapitelspalte im sind Verweise auf Zeilen in der untergeordneten **Recordset**, die die RELATE-Klausel erfüllen. Der gleiche Wert ist der *übergeordnete Spalte* von einer übergeordneten Zeile unverändert in die *untergeordneten Spalten* aller Zeilen der untergeordneten Kapitel. Wenn mehrere TO-Klauseln in derselben RELATE-Klausel verwendet werden, werden sie implizit die mithilfe eines AND-Operators kombiniert. Wenn die übergeordneten Spalten in der RELATE-Klausel keinen Schlüssel, der das übergeordnete Element dar, sind **Recordset**, eine einzelne untergeordnete Zeile kann mehrere übergeordnete Zeilen haben.  
  
 Wenn Sie den Verweis in der Kapitelspalte im zugreifen, ruft ADO automatisch die **Recordset** durch den Verweis dargestellt wird. Beachten Sie, dass in einem Befehl ohne Parameter aus, auch wenn das gesamte untergeordnete **Recordset** wurde abgerufen wird, enthält das Kapitel nur eine Teilmenge von Zeilen.  
  
 Wenn die angefügte Spalte kein *Kapitel-Alias*, ein Namen wird automatisch für sie generiert werden. Ein [Feld](../../../ado/reference/ado-api/field-object.md) -Objekt für die Spalte angefügt wird die **Recordset** des Objekts [Felder](../../../ado/reference/ado-api/fields-collection-ado.md) Sammlung und den Datentyp werden **AdChapter**.  
  
 Informationen zum Navigieren durch eine hierarchische **Recordset**, finden Sie unter [den Zugriff auf Zeilen in einem hierarchischen Recordset](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Beispiel für die datenstrukturierung](../../../ado/guide/data/data-shaping-example.md)   
 [Formale Grammatik für Formen](../../../ado/guide/data/formal-shape-grammar.md)   
 [Shape-Befehle im Allgemeinen](../../../ado/guide/data/shape-commands-in-general.md)
