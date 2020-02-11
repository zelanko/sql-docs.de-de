---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d9452ade90f6967dff6d72d5692efcf91b93154d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68057242"
---
# <a name="processing-sql-statements"></a>Verarbeiten von SQL-Anweisungen
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Vermeiden Sie die Verwendung dieses Features bei der Entwicklung neuer Anwendungen, und planen Sie das Ändern von Anwendungen, in denen diese Funktion derzeit verwendet wird Microsoft empfiehlt die Verwendung der Cursor-Funktionalität des Treibers.  
  
 Die ODBC-Cursor Bibliothek übergibt alle SQL-Anweisungen direkt an den Treiber, mit Ausnahme der folgenden:  
  
-   Positionierte UPDATE-und DELETE-Anweisungen  
  
-   **Select for Update** -Anweisungen  
  
-   SQL-Anweisungen im Batch Modus  
  
 Um positionierte UPDATE-und DELETE-Anweisungen auszuführen und den Cursor in einer Zeile zum Aufrufen von **SQLGetData** für diese Zeile zu positionieren, erstellt die Cursor Bibliothek eine gesuchte Anweisung, die die Zeile identifiziert.  
  
 Dieser Abschnitt enthält die folgenden Themen:  
  
-   [Verarbeiten von positionierten UPDATE- und DELETE-Anweisungen](../../../odbc/reference/appendixes/processing-positioned-update-and-delete-statements.md)  
  
-   [Verarbeiten von SELECT FOR UPDATE-Anweisungen](../../../odbc/reference/appendixes/processing-select-for-update-statements.md)  
  
-   [Verarbeiten von Batches von SQL-Anweisungen](../../../odbc/reference/appendixes/processing-batches-of-sql-statements.md)  
  
-   [Erstellen von searched-Anweisungen](../../../odbc/reference/appendixes/constructing-searched-statements.md)
