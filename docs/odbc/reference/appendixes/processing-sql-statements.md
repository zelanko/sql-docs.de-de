---
description: Verarbeiten von SQL-Anweisungen
title: Verarbeiten von SQL-Anweisungen | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 381bb7bbc27fc74b5d57fbb01b6a80f17305f5cc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483192"
---
# <a name="processing-sql-statements"></a>Verarbeiten von SQL-Anweisungen
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Vermeiden Sie die Verwendung dieses Features bei der Entwicklung neuer Anwendungen, und planen Sie das Ändern von Anwendungen, in denen diese Funktion derzeit verwendet wird Microsoft empfiehlt die Verwendung der Cursor-Funktionalität des Treibers.  
  
 Die ODBC-Cursor Bibliothek übergibt alle SQL-Anweisungen direkt an den Treiber, mit Ausnahme der folgenden:  
  
-   Positionierte UPDATE-und DELETE-Anweisungen  
  
-   **Select for Update** -Anweisungen  
  
-   SQL-Anweisungen im Batch Modus  
  
 Um positionierte UPDATE-und DELETE-Anweisungen auszuführen und den Cursor in einer Zeile zum Aufrufen von **SQLGetData** für diese Zeile zu positionieren, erstellt die Cursor Bibliothek eine gesuchte Anweisung, die die Zeile identifiziert.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Processing Positioned Update and Delete Statements (Verarbeiten einer positionierten Aktualisierung und von DELETE-Anweisungen)](../../../odbc/reference/appendixes/processing-positioned-update-and-delete-statements.md)  
  
-   [Processing SELECT FOR UPDATE Statements (Verarbeiten der Anweisung SELECT FOR UPDATE)](../../../odbc/reference/appendixes/processing-select-for-update-statements.md)  
  
-   [Processing Batches of SQL Statements (Verarbeiten von Batches von SQL-Anweisungen)](../../../odbc/reference/appendixes/processing-batches-of-sql-statements.md)  
  
-   [Erstellen von komplexen Anweisungen](../../../odbc/reference/appendixes/constructing-searched-statements.md)
