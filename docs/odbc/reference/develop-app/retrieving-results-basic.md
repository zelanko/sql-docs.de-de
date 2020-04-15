---
title: Abrufen von Ergebnissen (Basic) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3f7d01bf92fcee07940e449a2fb4bbac4f0fe6ac
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304331"
---
# <a name="retrieving-results-basic"></a>Abrufen von Ergebnissen (Standard)
Ein *Resultset* ist eine Reihe von Zeilen in der Datenquelle, die bestimmten Kriterien entspricht. Es handelt sich um eine konzeptionelle Tabelle, die sich aus einer Abfrage ergibt und für eine Anwendung in tabellarischer Form verfügbar ist. **SELECT-Anweisungen,** Katalogfunktionen und einige Prozeduren erstellen Resultsets. Im folgenden Beispiel erstellt die erste SQL-Anweisung ein Resultset, das alle Zeilen und alle Spalten in der Tabelle Orders enthält, und die zweite SQL-Anweisung erstellt ein Resultset, das OrderID-, SalesPerson- und Statusspalten für die Zeilen in der Tabelle Orders enthält, in der der Status OPEN lautet:  
  
```  
SELECT * FROM Orders  
SELECT OrderID, SalesPerson, Status FROM Orders WHERE Status = 'OPEN'  
```  
  
 Ein Resultset kann leer sein, was sich von keinem Resultset unterscheidet. Die folgende SQL-Anweisung erstellt z. B. ein leeres Resultset:  
  
```  
SELECT * FROM Orders WHERE 1 = 2  
```  
  
 Ein leeres Resultset unterscheidet sich nicht von anderen Resultsets, außer dass es keine Zeilen hat. Beispielsweise kann die Anwendung Metadaten für das Resultset abrufen, versuchen, Zeilen abzurufen, und muss den Cursor über dem Resultset schließen.  
  
 Der Vorgang zum Abrufen von Zeilen aus der Datenquelle und deren Rückgabe an die Anwendung wird als *Abrufen*bezeichnet. In diesem Abschnitt werden die grundlegenden Teile dieses Prozesses erläutert. Informationen zu erweiterten Themen, z. B. Block- und Scrollable-Cursor, finden Sie unter [Cursor blockieren](../../../odbc/reference/develop-app/block-cursors.md) und [scrollbare Cursor .](../../../odbc/reference/develop-app/scrollable-cursors.md) Informationen zum Aktualisieren, Löschen und Einfügen von Zeilen finden Sie unter [Aktualisieren der Datenübersicht](../../../odbc/reference/develop-app/updating-data-overview.md).  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Wurde ein Resultset erstellt?](../../../odbc/reference/develop-app/was-a-result-set-created.md)  
  
-   [Resultsetmetadaten](../../../odbc/reference/develop-app/result-set-metadata.md)  
  
-   [Binden von Spalten](../../../odbc/reference/develop-app/binding-columns.md)  
  
-   [Abrufen von Daten](../../../odbc/reference/develop-app/fetching-data.md)  
  
-   [Schließen des Cursors](../../../odbc/reference/develop-app/closing-the-cursor.md)
