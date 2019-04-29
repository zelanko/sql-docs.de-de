---
title: SQL-Anweisungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], statement processing
- SQL statements [ODBC], cursor library
- cursor library [ODBC], statement processing
ms.assetid: 54dad6a3-e86c-477b-ba7c-4e95e0385ec1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5d5aa94062f90154126fb18c3658adb39bb1d5c0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63057049"
---
# <a name="processing-sql-statements"></a>Verarbeiten von SQL-Anweisungen
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 Die ODBC-Cursorbibliothek übergibt alle SQL-Anweisungen direkt an den Treiber aus, mit Ausnahme der folgenden:  
  
-   Positioniert Update und delete-Anweisungen  
  
-   **SELECT FOR UPDATE** Anweisungen  
  
-   SQL-Anweisungsbatches  
  
 Zum Ausführen von positionierten Aktualisierung und delete-Anweisungen und zur Positionierung des Cursors für eine Zeile aufrufen **SQLGetData** für diese Zeile, erstellt die Cursorbibliothek eine gesuchte-Anweisung, die die Zeile angibt.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Processing Positioned Update and Delete Statements (Verarbeiten einer positionierten Aktualisierung und von DELETE-Anweisungen)](../../../odbc/reference/appendixes/processing-positioned-update-and-delete-statements.md)  
  
-   [Processing SELECT FOR UPDATE Statements (Verarbeiten der Anweisung SELECT FOR UPDATE)](../../../odbc/reference/appendixes/processing-select-for-update-statements.md)  
  
-   [Processing Batches of SQL Statements (Verarbeiten von Batches von SQL-Anweisungen)](../../../odbc/reference/appendixes/processing-batches-of-sql-statements.md)  
  
-   [Erstellen von komplexen Anweisungen](../../../odbc/reference/appendixes/constructing-searched-statements.md)
