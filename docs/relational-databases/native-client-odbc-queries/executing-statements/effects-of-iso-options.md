---
title: Auswirkungen der ISO-Optionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ISO options (ODBC)
- ODBC applications, ISO options
- ODBC applications, statements
- SQL Server Native Client ODBC driver, ISO options
- statements [ODBC], ISO options
ms.assetid: 813f1397-fa0b-45ec-a718-e13fe2fb88ac
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 43347e4fcf517dc52c8791dc81220a8990e1655d
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73779865"
---
# <a name="effects-of-iso-options"></a>Effekte von ISO-Optionen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der ODBC-Standard orientiert sich eng am ISO-Standard, und ODBC-Anwendungen erwarten von einem ODBC-Treiber Standardverhalten. Um das Verhalten genauer zu gestalten, das im ODBC-Standard definiert ist, verwendet der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber immer alle ISO-Optionen, die in der-Version der SQL Server verfügbar sind, mit der er eine Verbindung herstellt.  
  
 Wenn der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]herstellt, erkennt der Server, dass der Client den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber verwendet, und legt mehrere Optionen für fest.  
  
 Der Treiber gibt diese Anweisungen selbst aus; die ODBC-Anwendung fordert sie nicht an. Durch das Einstellen dieser Optionen werden ODBC-Anwendungen, die den Treiber verwenden, besser portierbar, da das Serververhalten dem ISO-Standard entspricht.  
  
 DB-Library-basierte Anwendungen aktivieren diese Optionen im Allgemeinen nicht. Standorte, die unterschiedliche Verhaltensweisen zwischen ODBC-oder DB-Library-Clients beobachten, wenn Sie dieselbe SQL-Anweisung ausführen, sollten nicht davon ausgehen, dass dies auf ein Problem mit dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber Sie sollten die Anweisung zuerst in der DB-Library-Umgebung mit den gleichen SET-Optionen erneut ausführen, die vom [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber verwendet werden.  
  
 Da SET-Optionen jederzeit von Benutzern und Anwendungen aktiviert und deaktiviert werden können, sollten Entwickler von gespeicherten Prozeduren und Triggern diese mit den oben aufgeführten SET-Optionen sowohl im aktivierten als auch im deaktivierten Zustand testen. Dadurch wird sichergestellt, dass die Prozeduren und Trigger bei ihrem Aufruf korrekt ausgeführt werden, unabhängig davon, welche Optionen eine bestimmte Verbindung festgelegt hat. Wenn ein Trigger oder eine gespeicherte Prozedur eine bestimmte Einstellung für eine dieser Optionen erfordert, sollte am Anfang des Triggers bzw. der gespeicherten Prozedur eine SET-Anweisung ausgeführt werden. Die SET-Anweisung behält ihre Gültigkeit nur während der Ausführung des Triggers bzw. der gespeicherten Prozedur bei. Wenn der Trigger oder die Prozedur beendet ist, wird die ursprüngliche Einstellung wiederhergestellt.  
  
 Wenn eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hergestellt wird, wird zudem eine vierte SET-Option, CONCAT_NULL_YIELDS_NULL, aktiviert. Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber legt diese Optionen nicht fest, wenn AnsiNPW = NO in der Datenquelle oder entweder auf [SQLDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md) oder [sqlbrowseconnetct](../../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md)festgelegt ist.  
  
 Wie bei den zuvor notierten ISO-Optionen wird der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber die QUOTED_IDENTIFIER-Option nicht aktiviert, wenn QuotedID = No in der Datenquelle oder entweder in **SQLDriverConnect** oder **SQLBrowseConnect**angegeben ist.  
  
 Damit der Treiber den aktuellen Status der SET-Optionen ermitteln kann, sollten ODBC-Anwendungen die [!INCLUDE[tsql](../../../includes/tsql-md.md)] SET-Anweisung nicht verwenden, um diese Optionen festzulegen. Sie sollten diese Optionen nur mithilfe der Datenquelle oder über die Verbindungsoptionen festlegen. Wenn die Anwendung SET-Anweisungen ausgibt, generiert der Treiber möglicherweise falsche SQL-Anweisungen.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von &#40;ODBC&#41; -Anweisungen](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)   
 [SQLDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md)   
 [SQLBrowseConnect](../../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md)  
  
  
