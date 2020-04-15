---
title: Einschränkungen bei der Verwendung von Keyset-gesteuerten Cursorn | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], cursors
- keyset-driven cursors [ODBC]
ms.assetid: 59d86fed-387c-4719-9550-36343e74da44
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2aeb5a0c50192118dfff8ed7d866c3911c2b4007
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284150"
---
# <a name="limitations-of-using-keyset-driven-cursors"></a>Einschränkungen der Verwendung keysetgesteuerter Cursor
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Sie müssen in der Lage sein, eine einzelne ROWID-Spalte für die abgefragte Tabelle abzurufen. Ein Keyset-gesteuerter Cursor kann nicht für Verknüpfungen, Abfragen oder Anweisungen verwendet werden, die DISTINCT-, GROUP BY-, UNION-, INTERSECT- oder MINUS-Klauseln enthalten.  
  
 Wenn Ihre Anwendung Tabellenaliase verwendet, funktionieren Keyset-gesteuerte Cursor nicht. Vorwärts- oder statische Cursortypen sind erforderlich. Die Verwendung des Keyset-Cursortyps mit Tabellenaliasen führt zu folgendem Fehler: "[Microsoft][ODBC-Treiber für Oracle]Keyset-gesteuerter Cursor kann nicht beim Verbinden, mit Union, Überschneiden oder Minus oder beim schreibgeschützten Resultset verwendet werden."  
  
> [!NOTE]  
>  Aufgrund der Art und Weise, wie der Treiber die SQL-Anweisung verarbeitet, die an den Oracle-Server gesendet wird, gibt Oracle intern die folgende Fehlermeldung zurück: "ORA-00964: Tabellenname nicht in DER FROM-Liste."
