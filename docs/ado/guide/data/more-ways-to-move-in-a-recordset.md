---
title: Weitere Informationen zum Verschieben in einem Recordset | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- MoveNext method [ADO]
- MoveLast method [ADO]
- MoveFirst method [ADO]
- Recordset object [ADO], moving
- MovePrevious method [ADO]
ms.assetid: 9f8cf1b2-3def-453f-a0ff-4646c5f15262
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 8cb2edebfd0a23f7b626dfdc4cb55eab9684a2c0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66700815"
---
# <a name="more-ways-to-move-in-a-recordset"></a>Weitere Möglichkeiten zum Navigieren in einem Recordset
Die folgenden vier Methoden werden zum Verschieben oder einen Bildlauf durchführen, ist in der **Recordset**: [MoveFirst, MoveLast, MoveNext und MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md). (Einige dieser Methoden sind nicht verfügbar für Vorwärtscursor.)  
  
 **MoveFirst** ändert sich die Position des aktuelle Datensatzes in den ersten Datensatz in die **Recordset**. **MoveLast** Notieren Sie die Änderungen des aktuellen Datensatzes auf die letzte position in der **Recordset**. Verwendung von **MoveFirst** oder **MoveLast**, **Recordset** -Objekt Lesezeichen oder Bewegung des Cursors von Abwärtskompatibilität unterstützt; andernfalls wird der Methodenaufruf ein Fehler generiert.  
  
 **MoveNext** verschiebt den aktuellen Datensatz positionieren zentral weiterleiten. Notieren Sie auf der letzten beim Aufruf **MoveNext**, **EOF** festgelegt **"true"** . **MovePrevious** verschiebt den aktuellen Datensatz positionieren zentral rückwärts. Wenn Sie für den ersten Datensatz, beim Aufrufen sind **MovePrevious**, **BOF** festgelegt **"true"** . Es ist ratsam, überprüfen Sie die **EOF** und **BOF** Eigenschaften, die bei Verwendung dieser Methoden und den Cursor zurück zu einer gültigen Position des aktuellen Datensatzes verschieben, wenn Sie sich über das Ende des Verschieben der **Recordset**wie hier gezeigt:  
  
```  
. . .  
oRs.MoveNext  
If oRs.EOF Then oRs.MoveLast  
. . .   
```  
  
 Oder, im Fall von der **MovePrevious** Methode:  
  
```  
. . .   
oRs.MovePrevious  
If oRs.BOF Then oRs.MoveFirst  
. . .  
```  
  
 In Fällen, in denen die **Recordset** gefiltert oder sortiert wurde, und die Daten des aktuellen Datensatzes geändert werden, werden möglicherweise auch die Position ändern. In solchen Fällen die **MoveNext** Methode funktioniert normal, aber beachten Sie, dass die Position verschoben ist vorwärts aus die neue Position, nicht die alte Position aufzeichnen. Die Daten in den aktuellen Datensatz, z. B. durch ändern, dass der Datensatz, an das Ende der sortierten verschoben wird **Recordset**, würde bedeuten, dass der Aufruf **MoveNext** führt zu ADO durch Festlegen des aktuellen Datensatzes auf die die Position hinter dem letzten Datensatz in die **Recordset** (**EOF** =  **"true"** ).  
  
 Das Verhalten der verschiedenen Methoden der Verschiebung der **Recordset** Objekt abhängig ist, zu einem gewissen Grad, der Daten in die **Recordset**. Neue Datensätze hinzugefügt werden, um die **Recordset** werden zunächst in einer bestimmten Reihenfolge, die von der Datenquelle definiert ist und möglicherweise implizit abhängige oder explizit auf die Daten im neuen Datensatz hinzugefügt. Z. B. wenn eine Sortierung oder ein Join erfolgt in der Abfrage, die Daten lädt, die **Recordset**, wird der neue Datensatz eingefügt werden, an der entsprechenden Stelle in der **Recordset**. Wenn die Sortierung nicht explizit angegeben wird beim Erstellen der **Recordset**, Änderungen in der Data-Source-Implementierung muss möglicherweise die Reihenfolge der zurückgegebenen Zeilen um versehentlich zu ändern. In Addition, sortieren, Filtern und Bearbeitungsfunktionen von der **Recordset** können beeinflussen die Reihenfolge und möglicherweise die Zeilen im Recordset angezeigt werden.  
  
 Aus diesem Grund **MoveNext**, **MovePrevious**, **MoveFirst**, **MoveLast**, und **verschieben** sind Unterscheidung nach Kanatyp an andere Vorgänge ausgeführt werden, auf dem gleichen **Recordset**. ADO versuchen immer, verwalten Ihre aktuelle Position, bis Sie sie explizit verschieben, aber in manchen Fällen zwischenzeitliche Änderungen es schwierig machen, die Auswirkungen einer nachfolgenden Verschiebung zu verstehen. Wenn Sie aufrufen, z. B. **MoveFirst** an Position in der ersten Zeile mit einer sortierten **Recordset** und Sie die Sortierung in aufsteigender Reihenfolge, in absteigender Reihenfolge ändern, Sie befinden sich weiterhin auf der gleichen Zeile - aber nun ist es die letzte Zeile in der **Recordset**. **MoveFirst** , gelangen Sie zu einer anderen Zeile (die neue erste Zeile).  
  
 Ein weiteres Beispiel: Wenn Sie auf eine bestimmte Zeile in der Mitte der positioniert sind eine **Recordset** und rufen Sie **löschen** und rufen dann **MoveNext**, Sie sind jetzt für den Datensatz unmittelbar nach den gelöschten Datensatz. Aber ein Aufruf **MovePrevious** wird der Datensatz vor dem Sie den aktuellen Datensatz gelöscht, da der gelöschte Datensatz nicht mehr in der aktiven Mitgliedschaft gezählt wird die **Recordset**.  
  
 Es ist besonders schwierig, konsistente Move-Semantik für alle Anbieter für Methoden zu definieren, die relativ zum aktuellen Datensatz - verschieben **MovePrevious**, **MoveNext**, und **Verschieben** – bei Änderung von Daten in den aktuellen Datensatz. Filtern Sie beispielsweise bei Verwendung mit einer sortierten **Recordset**, und ändern Sie die Daten im aktuellen Datensatz, damit sie alle anderen Datensätze vorausgehen würde, aber Ihr geänderten Daten auch nicht mehr dem Filter entspricht, wo nicht eindeutig ein **MoveNext** Vorgang sollten Sie dauern. Die sicherste Lösung besteht darin, relative Bewegung in einer **Recordset** riskanter als absolute Bewegung ist (z. B. **MoveFirst** oder **MoveLast**) Wenn die Daten sind Ändern von während Datensätze bearbeitet werden, hinzugefügt oder gelöscht werden. Sortieren und Filtern von sollte auf eine primary key- oder die ID, basieren, da diese Art von Wert nicht ändern soll.
