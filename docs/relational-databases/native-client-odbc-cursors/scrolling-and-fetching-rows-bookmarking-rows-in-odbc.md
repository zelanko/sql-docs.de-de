---
title: Lesezeichenzeilen in ODBC | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], fetching rows
- ODBC cursors, fetching rows
- cursors [ODBC], scrolling rows
- ODBC cursors, scrolling rows
- bookmarks [ODBC]
ms.assetid: 9cfcd243-c9d4-4c2a-abc4-399dbabe5f6b
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0c1a4216d57d4f8178e55c54f7b0bcf61b8624c2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304001"
---
# <a name="scrolling-and-fetching-rows---bookmarking-rows-in-odbc"></a>Scrollen und Abrufen von Zeilen: Kennzeichnen von Zeilen in ODBC
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Ein Lesezeichen ist ein Wert, der verwendet wird, um eine Zeile mit Daten zu identifizieren. Die Bedeutung des Lesezeichenwerts ist nur dem Treiber oder der Datenquelle bekannt. Der Wert kann so einfach wie eine Zeilennummer oder so komplex wie eine Datenträgeradresse sein. In ODBC fordert die Anwendung ein Lesezeichen für bestimmte Zeilen an, speichert es und gibt es an den Cursor für die Rückgabe an die Zeile zurück.  
  
 Beim Abrufen von Zeilen mit [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)kann eine Anwendung eine Textmarke als Grundlage für die Auswahl der Startzeile verwenden. Dies ist eine Form der absoluten Adressierung, da sie nicht von der aktuellen Cursorposition abhängt. Um zu einer mit Lesezeichen versehenen Zeile zu scrollen, ruft die Anwendung **SQLFetchScroll** mit einem *FetchOrientation* von SQL_FETCH_BOOKMARK auf. Dieser Vorgang verwendet das Lesezeichen, auf das das SQL_ATTR_FETCH_BOOKMARK_PTR-Optionsattribut zeigt. Es gibt das Rowset zurück, das mit der Zeile beginnt, die von diesem Lesezeichen identifiziert wird. Eine Anwendung kann einen Offset für diesen Vorgang im *FetchOffset-Argument* des Aufrufs von **SQLFetchScroll**angeben. Wenn ein Offset angegeben ist, wird die erste Zeile des zurückgegebenen Rowsets durch Hinzufügen der Zahl im FetchOffset-Argument zu der Zahl der Zeile, die vom Lesezeichen identifiziert wird, bestimmt. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Native Client-ODBC-Treiber unterstützt nur Lesezeichen auf statischen und Keysetcursorn. Wenn beim Festlegen von Lesezeichen ein dynamischer Cursor angefordert wird, wird stattdessen ein Keysetcursor geöffnet.  
  
 Lesezeichen können auch mit der **SQLBulkOperations-Funktion** verwendet werden, um Vorgänge für eine Reihe von Zeilen auszuführen, die an der Textmarke beginnen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bildläufe und Abrufen von Zeilen](../../relational-databases/native-client-odbc-cursors/scrolling-and-fetching-rows.md)  
  
  
