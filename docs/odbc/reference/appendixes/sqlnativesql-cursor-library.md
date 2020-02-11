---
title: SQLNativeSql (Cursor Bibliothek) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLNativeSql function [ODBC], Cursor Library
ms.assetid: c4459092-1177-4b2a-b7f5-e0083d3bf2b2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0a8c42efbd87296cf7157d75d1848e4655247818
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68125711"
---
# <a name="sqlnativesql-cursor-library"></a>SQLNativeSql (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Vermeiden Sie die Verwendung dieses Features bei der Entwicklung neuer Anwendungen, und planen Sie das Ändern von Anwendungen, in denen diese Funktion derzeit verwendet wird Microsoft empfiehlt die Verwendung der Cursor-Funktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **SQLNativeSql** -Funktion in der Cursor Bibliothek erläutert. Allgemeine Informationen zu **SQLNativeSql**finden Sie unter [SQLNativeSql-Funktion](../../../odbc/reference/syntax/sqlnativesql-function.md).  
  
 Wenn der Treiber diese Funktion unterstützt, ruft die Cursor Bibliothek **SQLNativeSql** im Treiber auf und übergibt sie an die SQL-Anweisung. Für positioniertes Update, positioniertes löschen und **Select for Update** -Anweisungen wird die Anweisung von der Cursor Bibliothek geändert, bevor Sie an den Treiber übergeben wird.  
  
> [!NOTE]  
>  Die Cursor Bibliothek gibt nicht korrekt SQLSTATE 34000 (Ungültiger Cursor Name) zurück, wenn der Cursor Name in einer positionierten Update-oder DELETE-Anweisung ungültig ist, die im *instatementtext* -Argument von **SQLNativeSql**weitergegeben wird. **SQLNativeSql** ist nicht für die Rückgabe von Syntax Fehlern vorgesehen, die nur bei der Anweisungs Vorbereitung oder-Ausführung zurückgegeben werden.
