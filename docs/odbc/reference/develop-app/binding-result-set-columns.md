---
title: Binden von Resultsetspalten | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306361"
---
# <a name="binding-result-set-columns"></a>Binden von Resultsetspalten
Anwendungen können so viele oder weniger Spalten des Resultsets binden, wie Sie auswählen, einschließlich der Bindung überhaupt keiner Spalten. Wenn eine Daten Zeile abgerufen wird, gibt der Treiber die Daten für die gebundenen Spalten an die Anwendung zurück. Ob die Anwendung alle Spalten im Resultset bindet, hängt von der Anwendung ab. Beispielsweise haben Anwendungen, die Berichte generieren, normalerweise ein festes Format. solche Anwendungen erstellen ein Resultset, das alle im Bericht verwendeten Spalten enthält. Anschließend werden die Daten für alle diese Spalten gebunden und abgerufen. Anwendungen, die Bildschirme mit vollständiger Datenanzeige anzeigen, ermöglichen es Benutzern manchmal, zu entscheiden, welche Spalten angezeigt werden. solche Anwendungen erstellen ein Resultset, das alle Spalten enthält, die der Benutzer möglicherweise wünscht, aber binden und rufen Sie die Daten nur für die Spalten, die vom Benutzer ausgewählt wurden.  
  
 Daten können aus ungebundenen Spalten abgerufen werden, indem **SQLGetData**aufgerufen wird. Dies wird häufig zum Abrufen von Long-Daten aufgerufen, die oft die Länge eines einzelnen Puffers überschreiten und in Teilen abgerufen werden müssen.  
  
 Spalten können jederzeit gebunden werden, auch nachdem Zeilen abgerufen wurden. Die neuen Bindungen werden jedoch erst beim nächsten Abrufen einer Zeile wirksam. Sie werden nicht auf Daten aus bereits abgerufenen Zeilen angewendet.  
  
 Eine Variable bleibt an eine Spalte gebunden, bis eine andere Variable an die Spalte gebunden ist, bis die Bindung der Spalte durch Aufrufen von **SQLBindCol** mit einem NULL-Zeiger als Adresse der Variablen aufgehoben wird, bis alle Spalten aufgehoben werden, indem **SQLFreeStmt** mit der Option SQL_UNBIND oder bis zur Freigabe der Anweisung die Bindung aufgehoben wird. Aus diesem Grund muss die Anwendung sicherstellen, dass alle gebundenen Variablen gültig bleiben, solange Sie gebunden sind. Weitere Informationen finden Sie unter [zuordnen und Freigeben von Puffern](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md).  
  
 Da Spalten Bindungen nur Informationen sind, die der Anweisungs Struktur zugeordnet sind, können Sie in beliebiger Reihenfolge festgelegt werden. Sie sind auch unabhängig vom Resultset. Nehmen wir beispielsweise an, dass eine Anwendung die Spalten des Resultsets bindet, das von der folgenden SQL-Anweisung generiert wird:  
  
```  
SELECT * FROM Orders  
```  
  
 Wenn die Anwendung dann die SQL-Anweisung ausführt.  
  
```  
SELECT * FROM Lines  
```  
  
 beim gleichen Anweisungs Handle sind die Spalten Bindungen für das erste Resultset weiterhin wirksam, da es sich dabei um die in der Anweisungs Struktur gespeicherten Bindungen handelt. In den meisten Fällen ist dies eine schlechte Programmierpraxis und sollte vermieden werden. Stattdessen sollte die Anwendung **SQLFreeStmt** mit der SQL_UNBIND-Option aufgerufen werden, um die Bindung aller alten Spalten aufzuheben und dann neue zu binden.
