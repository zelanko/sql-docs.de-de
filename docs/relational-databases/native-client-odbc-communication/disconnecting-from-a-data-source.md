---
title: Trennen der Verbindung mit einer Datenquelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d5a7cb061c308508b0ab5d489dcabb4b25f93883
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73784749"
---
# <a name="disconnecting-from-a-data-source"></a>Trennen der Verbindung mit einer Datenquelle
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Wenn eine Anwendung mit der Verwendung einer Datenquelle fertig ist, wird **SQLDisconnect**aufgerufen. **SQLDisconnect** gibt alle-Anweisungen frei, die der Verbindung zugeordnet sind, und trennt den Treiber von der Datenquelle. Nach dem Trennen der Verbindung kann die Anwendung [SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) aufzurufen, um das Verbindungs Handle freizugeben. Vor dem Beenden Ruft eine Anwendung auch **SQLFreeHandle** auf, um das Umgebungs Handle freizugeben.  
  
 Nach dem Trennen der Verbindung kann eine Anwendung das zugeordnete Verbindungshandle wiederverwenden. Hierbei kann entweder eine neue Verbindung zu derselben oder zu einer anderen Datenquelle aufgebaut werden. Sollte der Anwendungsentwickler entscheiden, die Verbindung aufrecht zu erhalten anstatt die Verbindung zu trennen und später wieder erneut herzustellen, sollte er dabei die relativen Kosten dieser Optionen in Betracht ziehen. Eine Verbindung mit einer Datenquelle herzustellen und aufrecht zu erhalten kann abhängig vom verwendeten Verbindungsmedium relativ kostspielig sein. Unter Berücksichtigung dieses Nachteils muss auch die Wahrscheinlichkeit erwogen werden, dass dieselbe Datenquelle unter Umständen von anderen Vorgängen beansprucht wird, und der Zeitpunkt dieser Nutzung bedacht werden. Eine Anwendung beansprucht möglicherweise auch mehr als eine Verbindung.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kommunikation mit SQL Server &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
  
