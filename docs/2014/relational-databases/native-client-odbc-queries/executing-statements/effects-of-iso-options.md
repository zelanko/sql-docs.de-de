---
title: Auswirkungen der ISO-Optionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: ebef85cf1deb2327122edfd536991f689b14c747
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "68206764"
---
# <a name="effects-of-iso-options"></a>Effekte von ISO-Optionen
  Der ODBC-Standard orientiert sich eng am ISO-Standard, und ODBC-Anwendungen erwarten von einem ODBC-Treiber Standardverhalten. Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber verwendet stets alle ISO-Optionen, die in der-Version von SQL Server verfügbar sind, mit der er eine Verbindung herstellt, damit das Verhalten stärker mit dem im ODBC-Standard definierten übereinstimmt.  
  
 Wenn der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber eine Verbindung mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]einer Instanz von herstellt, erkennt der Server, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] der Client den ODBC-Treiber von Native Client verwendet, und legt mehrere Optionen für fest.  
  
 Der Treiber gibt diese Anweisungen selbst aus; die ODBC-Anwendung fordert sie nicht an. Durch das Einstellen dieser Optionen werden ODBC-Anwendungen, die den Treiber verwenden, besser portierbar, da das Serververhalten dem ISO-Standard entspricht.  
  
 DB-Library-basierte Anwendungen aktivieren diese Optionen im Allgemeinen nicht. Standorte, die beim Ausführen derselben SQL-Anweisung unterschiedliche Verhaltensweisen zwischen ODBC-oder DB-Library-Clients beobachten, sollten nicht davon [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ausgehen, dass dies auf ein Problem mit dem Native Client ODBC-Treiber verweist. Sie sollten die Anweisung zuerst in der DB-Library-Umgebung mit den gleichen SET-Optionen erneut ausführen, die vom [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber verwendet werden.  
  
 Da SET-Optionen jederzeit von Benutzern und Anwendungen aktiviert und deaktiviert werden können, sollten Entwickler von gespeicherten Prozeduren und Triggern diese mit den oben aufgeführten SET-Optionen sowohl im aktivierten als auch im deaktivierten Zustand testen. Dadurch wird sichergestellt, dass die Prozeduren und Trigger bei ihrem Aufruf korrekt ausgeführt werden, unabhängig davon, welche Optionen eine bestimmte Verbindung festgelegt hat. Wenn ein Trigger oder eine gespeicherte Prozedur eine bestimmte Einstellung für eine dieser Optionen erfordert, sollte am Anfang des Triggers bzw. der gespeicherten Prozedur eine SET-Anweisung ausgeführt werden. Die SET-Anweisung behält ihre Gültigkeit nur während der Ausführung des Triggers bzw. der gespeicherten Prozedur bei. Wenn der Trigger oder die Prozedur beendet ist, wird die ursprüngliche Einstellung wiederhergestellt.  
  
 Wenn eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hergestellt wird, wird zudem eine vierte SET-Option, CONCAT_NULL_YIELDS_NULL, aktiviert. Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber legt diese Optionen für nicht fest, wenn AnsiNPW = NO in der Datenquelle oder entweder in [SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md) oder [sqlbrowseconnetct](../../native-client-odbc-api/sqlbrowseconnect.md)angegeben ist.  
  
 Wie bei den zuvor notierten ISO-Optionen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] schaltet der Native Client ODBC-Treiber die Option QUOTED_IDENTIFIER nicht ein, wenn QuotedID = No in der Datenquelle oder entweder in **SQLDriverConnect** oder **SQLBrowseConnect**angegeben ist.  
  
 Damit der Treiber den aktuellen Status der SET-Optionen ermitteln kann, sollten ODBC-Anwendungen die [!INCLUDE[tsql](../../../includes/tsql-md.md)] SET-Anweisung nicht verwenden, um diese Optionen festzulegen. Sie sollten diese Optionen nur mithilfe der Datenquelle oder über die Verbindungsoptionen festlegen. Wenn die Anwendung SET-Anweisungen ausgibt, generiert der Treiber möglicherweise falsche SQL-Anweisungen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen von Anweisungen &#40;ODBC-&#41;](executing-statements-odbc.md)   
 [SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md)   
 [SQLBrowseConnect](../../native-client-odbc-api/sqlbrowseconnect.md)  
  
  
