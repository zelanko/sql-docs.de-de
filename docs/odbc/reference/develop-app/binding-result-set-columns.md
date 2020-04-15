---
title: Bindungsergebnis-Set-Spalten | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], binding columns
- binding columns [ODBC]
ms.assetid: 4bc9c30f-83ae-4766-a746-032953c187ad
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 558ceb79d42d82477b70a028395de82cc023c170
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306361"
---
# <a name="binding-result-set-columns"></a>Binden von Resultsetspalten
Anwendungen können so viele oder so wenige Spalten des Resultsets binden, wie sie möchten, einschließlich der Bindung, die überhaupt keine Spalten enthält. Wenn eine Datenzeile abgerufen wird, gibt der Treiber die Daten für die gebundenen Spalten an die Anwendung zurück. Ob die Anwendung alle Spalten im Resultset bindet, hängt von der Anwendung ab. Beispielsweise haben Anwendungen, die Berichte generieren, in der Regel ein festes Format. Solche Anwendungen erstellen ein Resultset, das alle im Bericht verwendeten Spalten enthält, und binden und rufen dann die Daten für alle diese Spalten ab. Anwendungen, die Bildschirme voller Daten anzeigen, ermöglichen es dem Benutzer manchmal zu entscheiden, welche Spalten angezeigt werden sollen. Solche Anwendungen erstellen ein Resultset, das alle Spalten enthält, die der Benutzer möglicherweise möchte, binden und rufen die Daten jedoch nur für die vom Benutzer ausgewählten Spalten ab.  
  
 Daten können aus ungebundenen Spalten abgerufen werden, indem **SQLGetData**aufgerufen wird. Dies wird häufig aufgerufen, um lange Daten abzurufen, die oft die Länge eines einzelnen Puffers überschreiten und in Teilen abgerufen werden müssen.  
  
 Spalten können jederzeit gebunden werden, auch nachdem Zeilen abgerufen wurden. Die neuen Bindungen werden jedoch erst wirksam, wenn eine Zeile das nächste Mal abgerufen wird. Sie werden nicht auf Daten aus bereits abgerufenen Zeilen angewendet.  
  
 Eine Variable bleibt an eine Spalte gebunden, bis eine andere Variable an die Spalte gebunden ist, bis die Spalte durch Aufrufen von **SQLBindCol** mit einem NULL-Zeiger als Adresse der Variablen aufgehoben wird, bis alle Spalten durch Aufrufen von **SQLFreeStmt** mit der Option SQL_UNBIND oder bis die Anweisung freigegeben wird, nicht gebunden sind. Aus diesem Grund muss die Anwendung sicherstellen, dass alle gebundenen Variablen gültig bleiben, solange sie gebunden sind. Weitere Informationen finden Sie unter [Zuweisen und Verteilen von Puffern](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md).  
  
 Da Spaltenbindungen nur Informationen sind, die der Anweisungsstruktur zugeordnet sind, können sie in beliebiger Reihenfolge festgelegt werden. Sie sind auch unabhängig vom Resultset. Angenommen, eine Anwendung bindet die Spalten des Resultsets, das durch die folgende SQL-Anweisung generiert wird:  
  
```  
SELECT * FROM Orders  
```  
  
 Wenn die Anwendung dann die SQL-Anweisung  
  
```  
SELECT * FROM Lines  
```  
  
 für das gleiche Anweisungshandle sind die Spaltenbindungen für das erste Resultset weiterhin wirksam, da dies die bindungen sind, die in der Anweisungsstruktur gespeichert sind. In den meisten Fällen ist dies eine schlechte Programmierpraxis und sollte vermieden werden. Stattdessen sollte die Anwendung **SQLFreeStmt** mit der SQL_UNBIND Option aufrufen, um alle alten Spalten zu binden und dann neue zu binden.
