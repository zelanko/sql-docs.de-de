---
title: Zuordnen eines Anweisungs Handles | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetStmtAttr function
- statements [ODBC], statement handles
- ODBC applications, executing queries
- SQLGetStmtAttr function
- SQL Server Native Client ODBC driver, statements
- allocating statement handles
- ODBC applications, statements
- statement handles [ODBC]
- SQLAllocHandle function
ms.assetid: 9ee207f3-2667-45f5-87ca-e6efa1fd7a5c
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5c176536675af707ec2e16fde80028beba8a019a
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73779993"
---
# <a name="allocating-a-statement-handle"></a>Zuordnen eines Anweisungshandles
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Bevor eine Anwendung eine Anweisung ausführen kann, muss sie ein Anweisungshandle zuordnen. Dies geschieht durch Aufrufen von **sqlzuordchandle** , wobei der Parameter " *typtype* " auf "SQL_HANDLE_STMT" festgelegt ist und " *InputHandle* " auf ein Verbindungs Handle verweist.  
  
 Anweisungsattribute sind Eigenschaften des Anweisungshandles. Beispielanweisungsattribute können die Verwendung von Lesezeichen und den mit dem Resultset der Anweisung zu verwendenden Cursor beinhalten. Anweisungs Attribute werden mit [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)festgelegt, und ihre aktuellen Einstellungen werden mithilfe von [SQLGetStmtAttr](../../relational-databases/native-client-odbc-api/sqlgetstmtattr.md)abgerufen. Es ist nicht erforderlich, dass eine Anwendung Anweisungsattribute festlegt; alle Anweisungsattribute haben Standardwerte und einige sind treiberspezifisch.  
  
 Gehen Sie bei der Verwendung mehrere ODBC-Anweisungs- und -Verbindungsoptionen vorsichtig vor. Der Aufruf von [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) mit auf SQL_ATTR_LOGIN_TIMEOUT festgelegter *fOption* steuert die Zeit, die eine Anwendung auf einen Timeout Timeout wartet, während darauf gewartet wird, dass eine Verbindung hergestellt wird (0 gibt eine unbegrenzte Wartezeit an). Für Sites mit langen Reaktionszeiten kann hierfür ein hoher Wert festgelegt werden, um sicherzustellen, dass zum Herstellen von Verbindungen ausreichend Zeit eingeräumt wird. Jedoch sollte das Intervall stets so niedrig sein, dass der Benutzer nach einer angemessenen Zeitspanne benachrichtig wird, wenn der Treiber keine Verbindung herstellen kann.  
  
 Wenn Sie **SQLSetStmtAttr** aufrufen, wobei *fOption* auf SQL_ATTR_QUERY_TIMEOUT festgelegt ist, wird ein Abfrage Timeout Intervall festgelegt, um den Server und den Benutzer vor Abfragen mit langer Laufzeit zu schützen.  
  
 Wenn Sie **SQLSetStmtAttr** aufrufen, wobei *fOption* auf SQL_ATTR_MAX_LENGTH festgelegt ist, wird die Menge an **Text** -und **Bilddaten** , die eine einzelne Anweisung abrufen kann, eingeschränkt. Wenn Sie **SQLSetStmtAttr** aufrufen, wobei *fOption* auf SQL_ATTR_MAX_ROWS festgelegt ist, schränkt auch ein Rowset auf die ersten *n* Zeilen ein, wenn dies alles ist, was die Anwendung erfordert. Beachten Sie, dass das Festlegen von SQL_ATTR_MAX_ROWS bewirkt, dass der Treiber eine SET ROWCOUNT-Anweisung an den Server ausgibt. Dies wirkt sich auf alle [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anweisungen aus, einschließlich Triggern und Updates.  
  
 Gehen Sie beim Festlegen dieser Optionen vorsichtig vor. Im Idealfall sollten alle Anweisungshandle eines Verbindungshandles die gleichen Einstellungen für SQL_ATTR_MAX_LENGTH und SQL_ATTR_MAX_ROWS aufweisen. Wenn der Treiber von einem Anweisungshandle zu einem anderen mit abweichenden Werten für diese Optionen wechselt, muss der Treiber die entsprechenden SET TEXTSIZE- und SET ROWCOUNT-Anweisungen generieren, um die Einstellungen zu ändern. Der Treiber kann diese Anweisungen nicht dem gleichen Batch zuordnen, in dem sich auch die SQL-Anweisung des Benutzers befindet, da die SQL-Anweisung des Benutzers eine Anweisung enthalten kann, die die erste Anweisung in einem Batch darstellen muss. Der Treiber muss die Anweisungen SET TEXTSIZE und SET ROWCOUNT in einem separaten Batch senden, der automatisch einen zusätzlichen Roundtrip zum Server generiert.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von &#40;Abfragen (ODBC)&#41;](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
