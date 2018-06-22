---
title: Kennzeichnen von Zeilen in ODBC | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], fetching rows
- ODBC cursors, fetching rows
- cursors [ODBC], scrolling rows
- ODBC cursors, scrolling rows
- bookmarks [ODBC]
ms.assetid: 9cfcd243-c9d4-4c2a-abc4-399dbabe5f6b
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7f2d19fe6cf79e11c11a5e6c5c4839ae35788353
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36057840"
---
# <a name="bookmarking-rows-in-odbc"></a>Kennzeichnen von Zeilen in ODBC
  Ein Lesezeichen ist ein Wert, der verwendet wird, um eine Zeile mit Daten zu identifizieren. Die Bedeutung des Lesezeichenwerts ist nur dem Treiber oder der Datenquelle bekannt. Der Wert kann so einfach wie eine Zeilennummer oder so komplex wie eine Datenträgeradresse sein. In ODBC fordert die Anwendung ein Lesezeichen für bestimmte Zeilen an, speichert es und gibt es an den Cursor für die Rückgabe an die Zeile zurück.  
  
 Beim Abrufen von Zeilen mit [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md), eine Anwendung kann einem Lesezeichen als Basis für die Auswahl der Startzeile verwenden. Dies ist eine Form der absoluten Adressierung, da sie nicht von der aktuellen Cursorposition abhängt. Um einen Bildlauf zu einer Lesezeichen versehenen Zeile, die Anwendung ruft **SQLFetchScroll** mit einem *FetchOrientation* von sql_fetch_bookmark auf. Dieser Vorgang verwendet das Lesezeichen, auf das das SQL_ATTR_FETCH_BOOKMARK_PTR-Optionsattribut zeigt. Es gibt das Rowset zurück, das mit der Zeile beginnt, die von diesem Lesezeichen identifiziert wird. Eine Anwendung kann einen Offset für diesen Vorgang im Angeben der *FetchOffset* Argument des Aufrufs von **SQLFetchScroll**. Wenn ein Offset angegeben ist, wird die erste Zeile des zurückgegebenen Rowsets durch Hinzufügen der Zahl im FetchOffset-Argument zu der Zahl der Zeile, die vom Lesezeichen identifiziert wird, bestimmt. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Native Client-ODBC-Treiber unterstützt nur Lesezeichen auf statischen und Keysetcursorn. Wenn beim Festlegen von Lesezeichen ein dynamischer Cursor angefordert wird, wird stattdessen ein Keysetcursor geöffnet.  
  
 Lesezeichen können auch verwendet werden, mit der **SQLBulkOperations** Funktion zum Ausführen von Vorgängen für eine Gruppe von Zeilen, die beim Lesezeichen beginnen.  
  
## <a name="see-also"></a>Siehe auch  
 [Scrollen und Fetchen von Zeilen](../native-client-ole-db-rowsets/fetching-rows.md)  
  
  