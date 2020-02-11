---
title: SQLGetData (Cursor Bibliothek) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetData function [ODBC], Cursor Library
ms.assetid: ff40c9c0-b847-4426-a099-1bff47e6e872
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5962882de08712dcff75790de7c58d69f965a3bd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68086381"
---
# <a name="sqlgetdata-cursor-library"></a>SQLGetData (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Vermeiden Sie die Verwendung dieses Features bei der Entwicklung neuer Anwendungen, und planen Sie das Ändern von Anwendungen, in denen diese Funktion derzeit verwendet wird Microsoft empfiehlt die Verwendung der Cursor-Funktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **SQLGetData** -Funktion in der Cursor Bibliothek erläutert. Allgemeine Informationen zu **SQLGetData**finden Sie unter [SQLGetData-Funktion](../../../odbc/reference/syntax/sqlgetdata-function.md).  
  
 Die Cursor Bibliothek implementiert **SQLGetData** , indem zuerst eine **Select** -Anweisung mit einer **Where** -Klausel erstellt wird, die die im Cache gespeicherten Werte für jede gebundene Spalte in der aktuellen Zeile auflistet. Anschließend wird die **Select** -Anweisung ausgeführt, um die Zeile erneut auszuwählen, und **SQLGetData** wird im Treiber aufgerufen, um die Daten aus der Datenquelle abzurufen (im Gegensatz zum Cache).  
  
> [!CAUTION]  
>  Die **Where** -Klausel, die von der Cursor Bibliothek zum Identifizieren der aktuellen Zeile erstellt wurde, kann keine Zeilen identifizieren, eine andere Zeile identifizieren oder mehr als eine Zeile identifizieren. Weitere Informationen finden Sie unter [Erstellen von durchsuchten Anweisungen](../../../odbc/reference/appendixes/constructing-searched-statements.md).  
  
 Wenn das SQL_ATTR_USE_BOOKMARKS-Anweisungs Attribut auf SQL_UB_VARIABLE festgelegt ist, kann **SQLGetData** für Spalte 0 aufgerufen werden, um Lesezeichen Daten zurückzugeben.  
  
 Aufrufe von **SQLGetData** unterliegen den folgenden Einschränkungen:  
  
-   **SQLGetData** kann nicht für Vorwärts Cursor aufgerufen werden.  
  
-   **SQLGetData** kann nur aufgerufen werden, wenn die folgenden Bedingungen erfüllt sind: eine **Select** -Anweisung hat das Resultset generiert. die **Select** -Anweisung enthielt keine Join-, **Union** -oder **Group by** -Klausel. und alle Spalten, die einen Alias oder Ausdruck in der Auswahlliste verwendet haben, wurden nicht an **SQLBindCol**gebunden.  
  
-   Wenn der Treiber nur eine aktive Anweisung unterstützt, ruft die Cursor Bibliothek den Rest des Resultsets ab, bevor die **Select** -Anweisung ausgeführt und **SQLGetData**aufgerufen wird.
