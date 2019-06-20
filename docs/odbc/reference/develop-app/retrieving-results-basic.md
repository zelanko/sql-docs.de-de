---
title: Abrufen von Ergebnissen (Standard) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], about result sets
- data sources [ODBC], result sets
- empty result sets [ODBC]
ms.assetid: 052870e3-3f3f-4f07-91da-b649348225f4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8eb98d7c17663894e1bacdc27e431d6a54f45d3b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62468662"
---
# <a name="retrieving-results-basic"></a>Abrufen von Ergebnissen (Standard)
Ein *Resultset* ist ein Satz von Zeilen in der Datenquelle, die bestimmten Kriterien entsprechen. Es ist eine konzeptionelle Tabelle, die aus einer Abfrage führt in Tabellenform, die für eine Anwendung verfügbar ist. **Wählen Sie** -Anweisungen, Katalogfunktionen und einige Verfahren Resultsets zu erstellen. Im folgenden Beispiel ist die erste SQL-Anweisung erstellt ein Resultset mit der alle Zeilen und alle Spalten in der Orders-Tabelle, und die zweite SQL-Anweisung erstellt ein Resultset mit Spalten für OrderID, Vertriebsmitarbeiter und Status für die Zeilen in der Orders-Tabelle der Status in der offen ist:  
  
```  
SELECT * FROM Orders  
SELECT OrderID, SalesPerson, Status FROM Orders WHERE Status = 'OPEN'  
```  
  
 Ein Resultset kann leer sein, unterscheidet sich vom überhaupt kein Resultset. Die folgende SQL-Anweisung erstellt z. B. ein leeres Resultset:  
  
```  
SELECT * FROM Orders WHERE 1 = 2  
```  
  
 Ein leeres Resultset unterscheidet sich nicht von der alle anderen Resultsets mit dem Unterschied, dass sie keine Zeilen enthält. Die Anwendung z. B. Abrufen von Metadaten für das Resultset kann, kann versuchen, um Zeilen abzurufen und muss, schließen Sie den Cursor über das Resultset.  
  
 Der Prozess des Abrufens von Zeilen aus der Datenquelle und Rückgabe an die Anwendung heißt *abrufen*. Dieser Abschnitt erläutert die grundlegenden Teile dieses Prozesses. Informationen zu den Themen für fortgeschrittenere Benutzer, wie z. B. Blocks und bildlauffähigen Cursorn finden Sie unter [Blockcursor](../../../odbc/reference/develop-app/block-cursors.md) und [scrollfähige Cursor](../../../odbc/reference/develop-app/scrollable-cursors.md). Informationen zum Aktualisieren, löschen und Einfügen von Zeilen finden Sie unter [Übersicht über die Daten Aktualisierung](../../../odbc/reference/develop-app/updating-data-overview.md).  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Wurde ein Resultset erstellt?](../../../odbc/reference/develop-app/was-a-result-set-created.md)  
  
-   [Resultsetmetadaten](../../../odbc/reference/develop-app/result-set-metadata.md)  
  
-   [Binden von Spalten](../../../odbc/reference/develop-app/binding-columns.md)  
  
-   [Abrufen von Daten](../../../odbc/reference/develop-app/fetching-data.md)  
  
-   [Schließen des Cursors](../../../odbc/reference/develop-app/closing-the-cursor.md)
