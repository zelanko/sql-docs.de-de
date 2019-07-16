---
title: Einschränkungen bei der Verwendung keysetgesteuerter Cursor | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0c35f900faf1a30788b3642af3fdd65d672951d5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68054121"
---
# <a name="limitations-of-using-keyset-driven-cursors"></a>Einschränkungen der Verwendung keysetgesteuerter Cursor
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den ODBC-Treiber, die von Oracle bereitgestellt.  
  
 Sie müssen eine einzelne ROWID-Spalte, für der abgefragten Tabelle abrufen können. Ein keysetgesteuerter Cursor kann nicht verwendet werden, auf die Verknüpfungen, Abfragen oder Anweisungen mit DISTINCT, GROUP BY, UNION, INTERSECT oder MINUS-Klauseln.  
  
 Auch wenn Ihre Anwendung Tabellenaliase verwendet, funktioniert keysetgesteuerte Cursor nicht. vorwärts gerichtete oder statische Cursortypen sind erforderlich. Verwenden das Keyset Cursortyp mit Tabellenaliasnamen führt dazu, dass den folgenden Fehler: "[Microsoft] [ODBC-Treiber für Oracle] können keine keysetgesteuerten Cursors auf die Verknüpfung mit Union, intersect oder minus oder einem schreibgeschützten Resultset."  
  
> [!NOTE]  
>  Aufgrund der Art und Weise, die der Treiber die SQL-Anweisung führt, die mit dem Oracle-Server gesendet wird, gibt der Oracle intern die folgende Fehlermeldung zurück: "ORA-00964: Tabelle Name nicht in der Liste."
