---
title: Cursorverhalten | Microsoft Docs
ms.custom: ''
ms.date: 10/24/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f2e3400e52cd0b7574c07a3cf813b4cbca317df2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305466"
---
# <a name="cursor-behaviors"></a>Cursorverhalten
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ODBC unterstützt die ISO-Optionen für die Definition des Verhaltens von Cursorn durch Angabe ihrer Bildlauffähigkeit und Sensitivität. Diese Verhaltensweisen werden durch Festlegen der SQL_ATTR_CURSOR_SCROLLABLE- und SQL_ATTR_CURSOR_SENSITIVITY-Optionen für einen Aufruf von [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)angegeben. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber implementiert diese Optionen, indem er Servercursor mit den folgenden Eigenschaften anfordert.  
  
|Einstellungen für das Cursorverhalten|Angeforderte Servercursoreigenschaften|  
|------------------------------|---------------------------------------------|  
|SQL_SCROLLABLE und SQL_SENSITIVE|Keysetgesteuerter Cursor und versionsbasierte vollständige Parallelität|  
|SQL_SCROLLABLE und SQL_INSENSITIVE|Statischer Cursor und Parallelität READ_ONLY|  
|SQL_SCROLLABLE und SQL_UNSPECIFIED|Statischer Cursor und Parallelität READ_ONLY|  
|SQL_NONSCROLLABLE und SQL_SENSITIVE|Vorwärtscursor und versionsbasierte vollständige Parallelität|  
|SQL_NONSCROLLABLE und SQL_INSENSITIVE|Standardresultset (Vorwärts, schreibgeschützt)|  
|SQL_NONSCROLLABLE und SQL_UNSPECIFIED|Standardresultset (Vorwärts, schreibgeschützt)|  
  
 Versionsbasierte optimistische Parallelität erfordert eine **Zeitstempelspalte** in der zugrunde liegenden Tabelle. Wenn eine versionsbasierte optimistische Parallelitätssteuerung für eine Tabelle angefordert wird, die keine **Zeitstempelspalte** enthält, verwendet der Server eine wertbasierte optimistische Parallelität.  
  
## <a name="scrollability"></a>Bildlauffähigkeit  
 Wenn SQL_ATTR_CURSOR_SCROLLABLE auf SQL_SCROLLABLE festgelegt ist, unterstützt der Cursor alle verschiedenen Werte für den *FetchOrientation-Parameter* von [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md). Wenn SQL_ATTR_CURSOR_SCROLLABLE auf SQL_NONSCROLLABLE festgelegt ist, unterstützt der Cursor nur den *FetchOrientation-Wert* von SQL_FETCH_NEXT.  
  
## <a name="sensitivity"></a>Sensitivität  
 Wenn SQL_ATTR_CURSOR_SENSITIVITY auf SQL_SENSITIVE festgelegt ist, spiegelt der Cursor Datenänderungen wider, die vom aktuellen Benutzer oder über Commitvorgänge anderer Benutzer ausgeführt werden. Wenn SQL_ATTR_CURSOR_SENSITIVITY auf SQL_INSENSITIVE festgelegt ist, spiegelt der Cursor keine Datenänderungen wider.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden von Cursors (ODBC)](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md) [Cursor-Eigenschaften](properties/cursor-properties.md) 
  
  
