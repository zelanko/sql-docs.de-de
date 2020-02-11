---
title: Trennen der Verbindung mit einer Datenquelle | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63205678"
---
# <a name="disconnecting-from-a-data-source"></a>Trennen der Verbindung mit einer Datenquelle
  Wenn eine Anwendung mit der Verwendung einer Datenquelle fertig ist, wird **SQLDisconnect**aufgerufen. **SQLDisconnect** gibt alle-Anweisungen frei, die der Verbindung zugeordnet sind, und trennt den Treiber von der Datenquelle. Nach dem Trennen der Verbindung kann die Anwendung [SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md) aufzurufen, um das Verbindungs Handle freizugeben. Vor dem Beenden Ruft eine Anwendung auch **SQLFreeHandle** auf, um das Umgebungs Handle freizugeben.  
  
 Nach dem Trennen der Verbindung kann eine Anwendung das zugeordnete Verbindungshandle wiederverwenden. Hierbei kann entweder eine neue Verbindung zu derselben oder zu einer anderen Datenquelle aufgebaut werden. Sollte der Anwendungsentwickler entscheiden, die Verbindung aufrecht zu erhalten anstatt die Verbindung zu trennen und später wieder erneut herzustellen, sollte er dabei die relativen Kosten dieser Optionen in Betracht ziehen. Eine Verbindung mit einer Datenquelle herzustellen und aufrecht zu erhalten kann abhängig vom verwendeten Verbindungsmedium relativ kostspielig sein. Unter Berücksichtigung dieses Nachteils muss auch die Wahrscheinlichkeit erwogen werden, dass dieselbe Datenquelle unter Umständen von anderen Vorgängen beansprucht wird, und der Zeitpunkt dieser Nutzung bedacht werden. Eine Anwendung beansprucht möglicherweise auch mehr als eine Verbindung.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kommunikation mit SQL Server &#40;ODBC-&#41;](communicating-with-sql-server-odbc.md)  
  
  
