---
title: Abrufen von Ergebnissen (Erweitert) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- offsets [ODBC]
- result sets [ODBC], about result sets
- bind offsets [ODBC]
ms.assetid: bc00c379-71a7-407a-975c-898243f39bb6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 22a88a96b856ba0976dcb8600d26f78b772654bd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68020503"
---
# <a name="retrieving-results-advanced"></a>Abrufen von Ergebnissen (Erweitert)
Einer Anwendung angegeben werden, dass ein Offset hinzugefügt wird, um Daten pufferadressen und den entsprechenden Längenindikator gebunden Puffer behandelt, wenn **SQLBulkOperations**, **SQLFetch**,  **SQLFetchScroll**, oder **SQLSetPos** aufgerufen wird. Die Ergebnisse dieser Ergänzungen bestimmen, die Adressen, die bei diesen Vorgängen verwendet wird.  
  
 BIND-Offsets können eine Anwendung so ändern Sie die Bindungen ohne **SQLBindCol** für zuvor gebundene Spalten. Ein Aufruf von **SQLBindCol** zum Binden von Daten ändert sich die Pufferadresse und den Längenindikator /-Zeiger. Das erneute Binden mit einem Offset, fügt auf der anderen Seite einfach einen Offset auf die vorhandenen Pufferadresse für gebundene Daten und den Längenindikator/Pufferadresse. Wenn Offsets verwendet werden, die Bindungen sind eine "Vorlage" wie die Anwendungspuffer angeordnet werden, und der Anwendung kann auf unterschiedliche Bereiche des Arbeitsspeichers dieser "Template" verschieben, durch Ändern des Offsets. Ein neuer Offset kann zu einem beliebigen Zeitpunkt angegeben werden, und es wird immer hinzugefügt, die ursprünglich gebundenen Werte.  
  
 Um eine Bindung Offset anzugeben, legt die Anwendung das Anweisungsattribut SQL_ATTR_ROW_BIND_OFFSET_PTR an die Adresse eines Puffers SQLINTEGER fest. Bevor die Anwendung eine Funktion aufruft, die die Bindungen, wie z. B. verwendet **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**, oder **SQLSetPos**, platziert es einen Offset in Bytes, die in diesen Puffer, solange weder die Adresse des Puffers als auch die Pufferadresse Längenindikator/0 ist, und so lange die gebundene Spalte im Ergebnis festgelegt ist. Die Summe der Adresse und den Offset muss eine gültige Adresse sein. (Dies bedeutet, dass eine oder beide der Offset und die Adresse, die der Offset hinzugefügt wird, ungültig sein können, solange die Summe über eine gültige Adresse ist.) Das Anweisungsattribut SQL_ATTR_ROW_BIND_OFFSET_PTR ist ein Zeiger, damit Sie der Wert des Offsets für mehr als einen Satz von Binden von Daten, die geändert werden kann, indem eine Offset-Wert angewendet werden kann. Eine Anwendung muss sicherstellen, dass der Zeiger gültig bleibt, bis der Cursor geschlossen wird.  
  
> [!NOTE]  
>  Bindung Offsets werden vom ODBC-2 nicht unterstützt. *x* Treiber.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Blockcursor](../../../odbc/reference/develop-app/block-cursors.md)  
  
-   [Scrollbare Cursor](../../../odbc/reference/develop-app/scrollable-cursors.md)  
  
-   [Die ODBC-Cursorbibliothek](../../../odbc/reference/develop-app/the-odbc-cursor-library.md)  
  
-   [Mehrere Ergebnisse](../../../odbc/reference/develop-app/multiple-results.md)
