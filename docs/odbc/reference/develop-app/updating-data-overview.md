---
title: Aktualisieren einer Datenübersicht | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating data [ODBC], about updating data
- data updates [ODBC]
- updating data [ODBC]
- data updates [ODBC], about data updates
ms.assetid: 062036a4-cda6-4aaa-9765-f1ec3e0b31b1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3edbd41bc5361d864abcc7d631a90521af98ef01
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47777828"
---
# <a name="updating-data-overview"></a>Aktualisieren einer Datenübersicht
Anwendungen können Daten aktualisieren, entweder durch Ausführen von SQL-Anweisungen oder durch Aufrufen von **SQLSetPos** oder **SQLBulkOperations**. **UPDATE**, **löschen**, und **einfügen** -Anweisungen direkt in der Datenquelle reagieren und werden in der Regel von Treibern unterstützt. Durchsucht Update und Delete-Anweisungen enthalten, eine Spezifikation der Zeilen, die zu ändern. Positioniert Update und delete-Anweisungen und **SQLSetPos** wirken sich auf die Datenquelle über einen Cursor und weniger häufig verwendet werden.  
  
 Ob Cursor an das Resultset mit den Methoden, die in diesem Abschnitt beschriebenen vorgenommenen Änderungen erkannt werden können, hängt von den Typ des Cursors und Ihre Implementierung geht ab. Vorwärtscursor Zeilen nicht mehr zu, und alle Änderungen werden nicht erkannt. Weitere Informationen dazu, ob scrollbare Cursor Änderungen ermittelt werden können, finden Sie unter [scrollfähige Cursor](../../../odbc/reference/develop-app/scrollable-cursors.md).  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [UPDATE-, DELETE- und INSERT-Anweisungen](../../../odbc/reference/develop-app/update-delete-and-insert-statements.md)  
  
-   [Positionierte Aktualisierung und DELETE-Anweisung](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md)  
  
-   [Simulieren einer positionierten Aktualisierung und von DELETE-Anweisungen](../../../odbc/reference/develop-app/simulating-positioned-update-and-delete-statements.md)  
  
-   [Bestimmen der Anzahl der betroffenen Zeilen](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md)  
  
-   [Aktualisieren von Daten mit SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md)  
  
-   [Aktualisieren von Daten mit SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md)  
  
-   [Long-Daten, SQLSetPos und SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md)
