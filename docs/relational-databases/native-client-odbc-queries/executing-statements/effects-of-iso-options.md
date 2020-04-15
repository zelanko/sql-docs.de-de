---
title: Auswirkungen von ISO-Optionen | Microsoft Docs
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: adf37d03f5ea4f06be4d58e60deca68e10d45abb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297934"
---
# <a name="effects-of-iso-options"></a>Effekte von ISO-Optionen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der ODBC-Standard orientiert sich eng am ISO-Standard, und ODBC-Anwendungen erwarten von einem ODBC-Treiber Standardverhalten. Um sein Verhalten stärker an das im ODBC-Standard definierte zu halten, verwendet der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber immer alle ISO-Optionen, die in der Version von SQL Server verfügbar sind, mit dem er eine Verbindung herstellt.  
  
 Wenn [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] der Native Client ODBC-Treiber [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]eine Verbindung mit einer Instanz [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] von herstellt, erkennt der Server, dass der Client den Native Client ODBC-Treiber verwendet, und legt mehrere Optionen fest.  
  
 Der Treiber gibt diese Anweisungen selbst aus; die ODBC-Anwendung fordert sie nicht an. Durch das Einstellen dieser Optionen werden ODBC-Anwendungen, die den Treiber verwenden, besser portierbar, da das Serververhalten dem ISO-Standard entspricht.  
  
 DB-Library-basierte Anwendungen aktivieren diese Optionen im Allgemeinen nicht. Sites, die unterschiedliches Verhalten zwischen ODBC- oder DB-Library-Clients beobachten, wenn [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dieselbe SQL-Anweisung ausgeführt wird, sollten nicht davon ausgehen, dass dies auf ein Problem mit dem Native Client ODBC-Treiber verweist. Sie sollten die Anweisung zunächst in der DB-Library-Umgebung mit den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gleichen SET-Optionen wiederholen, die vom Native Client ODBC-Treiber verwendet werden.  
  
 Da SET-Optionen jederzeit von Benutzern und Anwendungen aktiviert und deaktiviert werden können, sollten Entwickler von gespeicherten Prozeduren und Triggern diese mit den oben aufgeführten SET-Optionen sowohl im aktivierten als auch im deaktivierten Zustand testen. Dadurch wird sichergestellt, dass die Prozeduren und Trigger bei ihrem Aufruf korrekt ausgeführt werden, unabhängig davon, welche Optionen eine bestimmte Verbindung festgelegt hat. Wenn ein Trigger oder eine gespeicherte Prozedur eine bestimmte Einstellung für eine dieser Optionen erfordert, sollte am Anfang des Triggers bzw. der gespeicherten Prozedur eine SET-Anweisung ausgeführt werden. Die SET-Anweisung behält ihre Gültigkeit nur während der Ausführung des Triggers bzw. der gespeicherten Prozedur bei. Wenn der Trigger oder die Prozedur beendet ist, wird die ursprüngliche Einstellung wiederhergestellt.  
  
 Wenn eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hergestellt wird, wird zudem eine vierte SET-Option, CONCAT_NULL_YIELDS_NULL, aktiviert. Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] native Client-ODBC-Treiber setzt diese Optionen nicht auf, wenn AnsiNPW=NO in der Datenquelle oder auf [SQLDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md) oder [SQLBrowseConnect](../../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md)angegeben ist.  
  
 Wie die zuvor erwähnten [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ISO-Optionen aktiviert der Native Client ODBC-Treiber die Option QUOTED_IDENTIFIER nicht, wenn QuotedID=NO in der Datenquelle oder auf **SQLDriverConnect** oder **SQLBrowseConnect**angegeben ist.  
  
 Damit der Treiber den aktuellen Status der SET-Optionen ermitteln kann, sollten ODBC-Anwendungen die [!INCLUDE[tsql](../../../includes/tsql-md.md)] SET-Anweisung nicht verwenden, um diese Optionen festzulegen. Sie sollten diese Optionen nur mithilfe der Datenquelle oder über die Verbindungsoptionen festlegen. Wenn die Anwendung SET-Anweisungen ausgibt, generiert der Treiber möglicherweise falsche SQL-Anweisungen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen von Anweisungen &#40;ODBC-&#41;](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)   
 [Sqldriverconnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md)   
 [SQLBrowseConnect](../../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md)  
  
  
