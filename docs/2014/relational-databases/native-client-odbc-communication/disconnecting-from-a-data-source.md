---
title: Trennen von einer Datenquelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC data sources, connections
- data sources [SQL Server Native Client]
- disconnecting [ODBC]
- ODBC applications, disconnecting
- SQLDisconnect function
- ODBC applications, data sources
- connections [SQL Server Native Client]
- SQLFreeHandle function
- ODBC data sources, disconnecting
- SQL Server Native Client ODBC driver, data sources
- ODBC functions
- SQL Server Native Client ODBC driver, connections
ms.assetid: 65b0267d-b2ab-4a59-83f2-436d90cfbf79
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 43ccc784d0d8759c559e705cbbb65861040f6e8a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48144730"
---
# <a name="disconnecting-from-a-data-source"></a>Trennen der Verbindung mit einer Datenquelle
  Wenn eine Anwendung mithilfe einer Datenquelle abgeschlossen ist, ruft er **SQLDisconnect**. **SQLDisconnect** gibt alle Anweisungen, die bei der Verbindung zugeordnet sind frei und trennt den Treiber aus der Datenquelle. Nach dem Trennen der Verbindung kann die Anwendung aufrufen kann [SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md) um das Verbindungshandle freizugeben. Vor dem Beenden, ruft eine Anwendung auch **SQLFreeHandle** um das Umgebungshandle freizugeben.  
  
 Nach dem Trennen der Verbindung kann eine Anwendung das zugeordnete Verbindungshandle wiederverwenden. Hierbei kann entweder eine neue Verbindung zu derselben oder zu einer anderen Datenquelle aufgebaut werden. Sollte der Anwendungsentwickler entscheiden, die Verbindung aufrecht zu erhalten anstatt die Verbindung zu trennen und später wieder erneut herzustellen, sollte er dabei die relativen Kosten dieser Optionen in Betracht ziehen. Eine Verbindung mit einer Datenquelle herzustellen und aufrecht zu erhalten kann abhängig vom verwendeten Verbindungsmedium relativ kostspielig sein. Unter Berücksichtigung dieses Nachteils muss auch die Wahrscheinlichkeit erwogen werden, dass dieselbe Datenquelle unter Umständen von anderen Vorgängen beansprucht wird, und der Zeitpunkt dieser Nutzung bedacht werden. Eine Anwendung beansprucht möglicherweise auch mehr als eine Verbindung.  
  
## <a name="see-also"></a>Siehe auch  
 [Kommunikation mit SQLServer &#40;ODBC&#41;](communicating-with-sql-server-odbc.md)  
  
  
