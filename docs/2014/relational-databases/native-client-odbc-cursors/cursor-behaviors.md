---
title: Cursor Verhalten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- scrollable cursors [SQL Server]
- SQL Server Native Client ODBC driver, cursors
- version-based optimistic concurrency
- cursors [ODBC], cursor behaviors
- ODBC applications, cursors
- SQL_ATTR_CURSOR_SENSITIVITY option
- SQL_ATTR_CURSOR_SCROLLABLE option
- sensitivity behavior of cursor
- ODBC cursors, cursor behaviors
ms.assetid: 742ddcd2-232b-4aa1-9212-027df120ad35
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7d6b41e72d3421d24a160dbcc226ce285e37981c
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82702045"
---
# <a name="cursor-behaviors"></a>Cursorverhalten
  ODBC unterstützt die ISO-Optionen für die Definition des Verhaltens von Cursorn durch Angabe ihrer Bildlauffähigkeit und Sensitivität. Diese Verhaltensweisen werden angegeben, indem die Optionen SQL_ATTR_CURSOR_SCROLLABLE und SQL_ATTR_CURSOR_SENSITIVITY bei einem [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)-Befehl festgelegt werden. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber implementiert diese Optionen, indem er Servercursor mit den folgenden Eigenschaften anfordert.  
  
|Einstellungen für das Cursorverhalten|Angeforderte Servercursoreigenschaften|  
|------------------------------|---------------------------------------------|  
|SQL_SCROLLABLE und SQL_SENSITIVE|Keysetgesteuerter Cursor und versionsbasierte vollständige Parallelität|  
|SQL_SCROLLABLE und SQL_INSENSITIVE|Statischer Cursor und Parallelität READ_ONLY|  
|SQL_SCROLLABLE und SQL_UNSPECIFIED|Statischer Cursor und Parallelität READ_ONLY|  
|SQL_NONSCROLLABLE und SQL_SENSITIVE|Vorwärtscursor und versionsbasierte vollständige Parallelität|  
|SQL_NONSCROLLABLE und SQL_INSENSITIVE|Standardresultset (Vorwärts, schreibgeschützt)|  
|SQL_NONSCROLLABLE und SQL_UNSPECIFIED|Standardresultset (Vorwärts, schreibgeschützt)|  
  
 Versions basierte vollständige Parallelität erfordert eine **Zeitstempel** -Spalte in der zugrunde liegenden Tabelle. Wenn eine Versions basierte vollständige Parallelitäts Steuerung für eine Tabelle angefordert wird, die keine **Zeitstempel** -Spalte aufweist, verwendet der Server wertebasierte vollständige Parallelität.  
  
## <a name="scrollability"></a>Bildlauffähigkeit  
 Wenn SQL_ATTR_CURSOR_SCROLLABLE auf SQL_SCROLLABLE festgelegt ist, unterstützt der Cursor alle unterschiedlichen Werte für den *FetchOrientation* -Parameter von [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md). Wenn SQL_ATTR_CURSOR_SCROLLABLE auf SQL_NONSCROLLABLE festgelegt ist, unterstützt der Cursor nur einen *FetchOrientation* -Wert von SQL_FETCH_NEXT.  
  
## <a name="sensitivity"></a>Sensitivität  
 Wenn SQL_ATTR_CURSOR_SENSITIVITY auf SQL_SENSITIVE festgelegt ist, spiegelt der Cursor Datenänderungen wider, die vom aktuellen Benutzer oder über Commitvorgänge anderer Benutzer ausgeführt werden. Wenn SQL_ATTR_CURSOR_SENSITIVITY auf SQL_INSENSITIVE festgelegt ist, spiegelt der Cursor keine Datenänderungen wider.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden von Cursorn &#40;ODBC-&#41;](using-cursors-odbc.md)  
  
  
