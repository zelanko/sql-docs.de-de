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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b92f317d72410a5dff56652dd9de1e3b2ba5c9cb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63199271"
---
# <a name="binding-result-set-columns"></a>Binden von Resultsetspalten
Anwendungen können binden, wie viele oder wenige Spalten des Resultsets, wie sie auswählen, einschließlich binden überhaupt keine Spalten. Wenn eine Datenzeile abgerufen wird, gibt der Treiber die Daten für die gebundenen Spalten für die Anwendung zurück. Gibt an, ob die Anwendung aller Spalten im Resultset bindet, hängt von der Anwendung ab. Anwendungen, die in der Regel Generieren von Berichten haben z. B. kein festes Format; solche Anwendungen erstellt ein Resultset enthält alle Spalten im Bericht verwendeten und binden Sie und die Daten für alle diese Spalten abrufen. Anwendungen, die Bildschirme, die vollständigen Daten, in einigen Fällen anzeigen können der Benutzer entscheiden, welche Spalten angezeigt; solche Anwendungen erstellen, ein Resultset mit allen Spalten, die der Benutzer kann jedoch binden und die Daten nur für diese Spalten, die vom Benutzer ausgewählten abrufen.  
  
 Daten können durch Aufrufen von ungebundenen Spalten abgerufen werden **SQLGetData**. Dieser Vorgang wird zum Abrufen von long-Daten, die häufig überschreitet die Länge eines einzelnen Puffers und in Teilen abgerufen werden muss.  
  
 Spalten können gebunden werden, jederzeit, auch nachdem Zeilen abgerufen wurden. Allerdings werden die neuen Bindungen nicht bis zum nächsten wirksam, die eine Zeile abgerufen wird; Sie sind nicht auf Daten aus bereits abgerufenen Zeilen angewendet.  
  
 Eine Variable an eine Spalte gebunden bleibt, bis eine andere Variable an die Spalte gebunden ist, bis die Spalte durch Aufrufen von nicht gebundenen ist **SQLBindCol** mit einem null-Zeiger als den Wert der Variablen-Adresse, bis alle Spalten aufgehoben werden, durch den Aufruf von **SQLFreeStmt** mit der Option SQL_UNBIND oder bis die Anweisung aufgehoben wird. Aus diesem Grund muss die Anwendung darauf achten, dass alle gebundene Variablen gültig bleiben, solange sie gebunden sind. Weitere Informationen finden Sie unter [zuweisen und Freigeben von Puffern](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md).  
  
 Da spaltenbindungen nur Informationen, die die Anweisung der Struktur zugeordnet sind, können sie in beliebiger Reihenfolge festgelegt werden. Sie sind auch unabhängige des Resultsets. Nehmen wir beispielsweise an, dass eine Anwendung die Spalten des Resultsets generiert, indem Sie die folgende SQL-Anweisung gebunden:  
  
```  
SELECT * FROM Orders  
```  
  
 Wenn die Anwendung dann die SQL-Anweisung ausgeführt wird.  
  
```  
SELECT * FROM Lines  
```  
  
 auf dem gleichen Anweisungshandle sind die spaltenbindungen für das erste Resultset immer noch wirksam, da dies die Bindungen in der Anweisung Struktur gespeichert sind. In den meisten Fällen Dies ist eine schlechte Programmiermethode und sollte vermieden werden. Stattdessen sollte die Anwendung aufrufen **SQLFreeStmt** mit der SQL_UNBIND-Option zum Aufheben der Bindung alle alten Spalten aus, und dann binden Sie neue.
