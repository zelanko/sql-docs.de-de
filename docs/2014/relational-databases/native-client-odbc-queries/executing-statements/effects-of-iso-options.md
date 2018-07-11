---
title: Effekte von ISO-Optionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ISO options (ODBC)
- ODBC applications, ISO options
- ODBC applications, statements
- SQL Server Native Client ODBC driver, ISO options
- statements [ODBC], ISO options
ms.assetid: 813f1397-fa0b-45ec-a718-e13fe2fb88ac
caps.latest.revision: 35
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ec72da4557bc851c833018cfff2cc53f8576da0b
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37411719"
---
# <a name="effects-of-iso-options"></a>Effekte von ISO-Optionen
  Der ODBC-Standard orientiert sich eng am ISO-Standard, und ODBC-Anwendungen erwarten von einem ODBC-Treiber Standardverhalten. Um ihr Verhalten besser entsprechen zu machen, die in der ODBC-Standard definiert die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber verwendet immer die ISO-Optionen zur Verfügung, in der Version von SQL Server, mit denen sie eine Verbindung herstellt.  
  
 Wenn die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber eine Verbindung herstellt, mit einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], vom Server erkannt, dass der Client die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber und aktiviert mehrere Optionen.  
  
 Der Treiber gibt diese Anweisungen selbst aus; die ODBC-Anwendung fordert sie nicht an. Durch das Einstellen dieser Optionen werden ODBC-Anwendungen, die den Treiber verwenden, besser portierbar, da das Serververhalten dem ISO-Standard entspricht.  
  
 DB-Library-basierte Anwendungen aktivieren diese Optionen im Allgemeinen nicht. Beobachten von verschiedenen Standorten verhaltensänderungen bei den verschiedenen ODBC oder DB-Library-Clients, wenn die gleiche SQL-Anweisung nicht gehen sollte verweist auf ein Problem mit der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber. Sie sollten zuerst erneut ausführen die Anweisung in der DB-Library-Umgebung mit denselben SET-Optionen von verwendet werden, würde die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber.  
  
 Da SET-Optionen jederzeit von Benutzern und Anwendungen aktiviert und deaktiviert werden können, sollten Entwickler von gespeicherten Prozeduren und Triggern diese mit den oben aufgeführten SET-Optionen sowohl im aktivierten als auch im deaktivierten Zustand testen. Dadurch wird sichergestellt, dass die Prozeduren und Trigger bei ihrem Aufruf korrekt ausgeführt werden, unabhängig davon, welche Optionen eine bestimmte Verbindung festgelegt hat. Wenn ein Trigger oder eine gespeicherte Prozedur eine bestimmte Einstellung für eine dieser Optionen erfordert, sollte am Anfang des Triggers bzw. der gespeicherten Prozedur eine SET-Anweisung ausgeführt werden. Die SET-Anweisung behält ihre Gültigkeit nur während der Ausführung des Triggers bzw. der gespeicherten Prozedur bei. Wenn der Trigger oder die Prozedur beendet ist, wird die ursprüngliche Einstellung wiederhergestellt.  
  
 Wenn eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hergestellt wird, wird zudem eine vierte SET-Option, CONCAT_NULL_YIELDS_NULL, aktiviert. Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber wird dieser Optionen auf, wenn nicht festgelegt AnsiNPW = NO angegeben ist, in der Datenquelle oder für [SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md) oder [SQLBrowseConnect](../../native-client-odbc-api/sqlbrowseconnect.md).  
  
 Die ISO-Optionen, wie die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber ist nicht aktiviert die QUOTED_IDENTIFIER-Option auf, wenn QuotedID = NO angegeben ist, in der Datenquelle oder für **SQLDriverConnect** oder  **SQLBrowseConnect**.  
  
 Damit der Treiber den aktuellen Status der SET-Optionen ermitteln kann, sollten ODBC-Anwendungen die [!INCLUDE[tsql](../../../includes/tsql-md.md)] SET-Anweisung nicht verwenden, um diese Optionen festzulegen. Sie sollten diese Optionen nur mithilfe der Datenquelle oder über die Verbindungsoptionen festlegen. Wenn die Anwendung SET-Anweisungen ausgibt, generiert der Treiber möglicherweise falsche SQL-Anweisungen.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von Anweisungen &#40;ODBC&#41;](executing-statements-odbc.md)   
 [SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md)   
 [SQLBrowseConnect](../../native-client-odbc-api/sqlbrowseconnect.md)  
  
  
