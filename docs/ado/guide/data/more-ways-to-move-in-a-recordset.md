---
description: Weitere Möglichkeiten zum Navigieren in einem Recordset
title: Weitere Möglichkeiten zum Verschieben in einem Recordset | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: e8c668bc24b388d0367429086416cd67b5355550
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88980291"
---
# <a name="more-ways-to-move-in-a-recordset"></a>Weitere Möglichkeiten zum Navigieren in einem Recordset
Die folgenden vier Methoden werden verwendet, um in das **Recordset**zu wechseln oder zu scrollen: [MoveFirst, MoveLast, MoveNext und MovePrevious](../../reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md). (Einige dieser Methoden sind bei Vorwärts Cursor nicht verfügbar.)  
  
 " **Muvefirst** " ändert die aktuelle Daten Satz Position in den ersten Datensatz im **Recordset**. " **Muvelast** " ändert die aktuelle Daten Satz Position in den letzten Datensatz im **Recordset**. Das **Recordset** -Objekt muss Lesezeichen oder rückwärts Cursor Bewegung unterstützen, um " **muvefirst** " oder " **muvelast**" zu verwenden. Andernfalls generiert der Methoden aufrufsvorgang einen Fehler.  
  
 Die aktuelle Daten Satz Position wird von " **muvenext** " um einen Ort vorwärts verschoben. Wenn Sie auf dem letzten Datensatz sind, wenn Sie " **wvenext**" aufgerufen haben, wird **EOF** auf " **true**" festgelegt. Mit " **muveprevious** " wird die aktuelle Daten Satz Position um eine Stelle nach hinten verschoben Wenn Sie auf dem ersten Datensatz sind, wenn Sie " **muveprevious**" aufgerufen haben, wird **BOF** auf " **true**" festgelegt. Es ist ratsam, die **EOF** -Eigenschaft und die **BOF** -Eigenschaft zu überprüfen, wenn Sie diese Methoden verwenden, und den Cursor zurück zu einer gültigen aktuellen Daten Satz Position zu bewegen, wenn Sie das Ende des **Recordsets**aus dem folgenden Beispiel entfernen:  
  
```  
. . .  
oRs.MoveNext  
If oRs.EOF Then oRs.MoveLast  
. . .   
```  
  
 Oder im Fall der Methode " **muveprevious** ":  
  
```  
. . .   
oRs.MovePrevious  
If oRs.BOF Then oRs.MoveFirst  
. . .  
```  
  
 In Fällen, in denen das **Recordset** gefiltert oder sortiert wurde und die Daten des aktuellen Datensatzes geändert werden, kann sich auch die Position ändern. In solchen Fällen funktioniert die Methode "Design **ext** " normal, aber beachten Sie, dass die Position einen Datensatz von der neuen Position nach oben verschoben wird, nicht die alte Position. Wenn z. b. die Daten im aktuellen Datensatz geändert werden, sodass der Datensatz an das Ende des sortierten **Recordsets**verschoben wird, bedeutet dies, dass der Aufruf von " **wvenext** " dazu führt, dass der aktuelle Datensatz von ADO auf die Position hinter dem letzten Datensatz im **Recordset** (**EOF**  =  **true**) festgelegt wird.  
  
 Das Verhalten der verschiedenen Verschiebungs Methoden des **Recordset** -Objekts hängt in gewissem Umfang von den Daten innerhalb des **Recordsets**ab. Neue Datensätze, die dem **Recordset** hinzugefügt werden, werden anfänglich in einer bestimmten Reihenfolge hinzugefügt, die von der Datenquelle definiert wird und implizit oder explizit von den Daten im neuen Datensatz abhängig sein kann. Wenn z. b. in der Abfrage, die das **Recordset auffüllt**, eine Sortierung oder ein Join ausgeführt wird, wird der neue Datensatz an der entsprechenden Stelle innerhalb des **Recordsets**eingefügt. Wenn die Reihenfolge beim Erstellen des **Recordsets**nicht explizit angegeben wird, können Änderungen in der Datenquellen Implementierung bewirken, dass die Reihenfolge der zurückgegebenen Zeilen versehentlich geändert wird. Darüber hinaus können die Sortierungs-, Filter-und Bearbeitungsfunktionen des **Recordsets** die Reihenfolge beeinflussen und möglicherweise die Zeilen im Recordset sichtbar werden.  
  
 Daher sind **MoveNext**, **MovePrevious**, **MoveFirst**, **MoveLast**und **Move** für andere Vorgänge sensibel, die für dasselbe **Recordset**ausgeführt werden. ADO versucht immer, Ihre aktuelle Position beizubehalten, bis Sie Sie explizit verschieben. manchmal ist es jedoch schwierig, die Auswirkungen einer nachfolgenden Verschiebung zu verstehen. Wenn Sie z. b. " **muvefirst** " anordnen, um die erste Zeile eines sortierten **Recordsets** zu positionieren, und Sie die Sortierung von aufsteigender in absteigender Reihenfolge ändern, befinden Sie sich immer noch in derselben Zeile, aber jetzt ist Sie die letzte Zeile im **Recordset**. Mit " **muvefirst** " gelangen Sie zu einer anderen Zeile (die neue erste Zeile).  
  
 Ein weiteres Beispiel: Wenn Sie in einer bestimmten Zeile in der Mitte eines **Recordsets** positioniert sind und **Löschen** und dann " **wvenext**" aufruft, befinden Sie sich jetzt im Datensatz direkt nach dem gelöschten Datensatz. Durch den Aufruf von " **muveprevious** " wird jedoch der Datensatz vorangestellt, der dem aktuellen Datensatz gelöscht wurde, da der gelöschte Datensatz nicht mehr in der aktiven Mitgliedschaft des **Recordsets**gezählt wird.  
  
 Es ist besonders schwierig, eine konsistente Verschiebungs Semantik für alle Anbieter für Methoden zu definieren, die relativ zum aktuellen Datensatz ( **MovePrevious**, **MoveNext**) und zum **verschieben** von Daten im aktuellen Datensatz verschoben werden. Wenn Sie z. b. mit einem sortierten, gefilterten **Recordset**arbeiten und die Daten im aktuellen Datensatz so ändern, dass Sie vor allen anderen Datensätzen stehen, die geänderten Daten aber ebenfalls nicht mehr mit dem Filter übereinstimmen, ist es nicht klar, an welcher **Stelle ein Vorgang** für einen Vorgang durchführt. Der sicherste Schluss ist, dass die relative Bewegung innerhalb eines **Recordsets** riskant ist als die absolute Verschiebung (z. b. die Verwendung von " **muvefirst** " oder " **muvelast**"), wenn sich die Daten ändern, während Datensätze bearbeitet, hinzugefügt oder gelöscht werden. Das Sortieren und Filtern sollte auf einem Primärschlüssel oder einer ID basieren, da dieser Werttyp nicht geändert werden sollte.