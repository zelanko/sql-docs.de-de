---
title: Zuweisen eines Anweisungshandles | Microsoft Docs
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 85678c5b03a77910c73bd5b8bac8d0e40d52c252
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81291604"
---
# <a name="allocating-a-statement-handle"></a>Zuordnen eines Anweisungshandles
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Bevor eine Anwendung eine Anweisung ausführen kann, muss sie ein Anweisungshandle zuordnen. Dazu ruft **sie SQLAllocHandle** auf, wobei der *Parameter HandleType* auf SQL_HANDLE_STMT und *InputHandle,* der auf ein Verbindungshandle verweist, festgelegt ist.  
  
 Anweisungsattribute sind Eigenschaften des Anweisungshandles. Beispielanweisungsattribute können die Verwendung von Lesezeichen und den mit dem Resultset der Anweisung zu verwendenden Cursor beinhalten. Anweisungsattribute werden mit [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)festgelegt, und ihre aktuellen Einstellungen werden mithilfe von [SQLGetStmtAttr](../../relational-databases/native-client-odbc-api/sqlgetstmtattr.md)abgerufen. Es ist nicht erforderlich, dass eine Anwendung Anweisungsattribute festlegt; alle Anweisungsattribute haben Standardwerte und einige sind treiberspezifisch.  
  
 Gehen Sie bei der Verwendung mehrere ODBC-Anweisungs- und -Verbindungsoptionen vorsichtig vor. Aufrufen [von SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) mit *fOption* auf SQL_ATTR_LOGIN_TIMEOUT steuert die Zeit, die eine Anwendung auf einen Verbindungsversuch wartet, während sie auf das Herstellen einer Verbindung wartet (0 gibt eine unendliche Wartezeit an). Für Sites mit langen Reaktionszeiten kann hierfür ein hoher Wert festgelegt werden, um sicherzustellen, dass zum Herstellen von Verbindungen ausreichend Zeit eingeräumt wird. Jedoch sollte das Intervall stets so niedrig sein, dass der Benutzer nach einer angemessenen Zeitspanne benachrichtig wird, wenn der Treiber keine Verbindung herstellen kann.  
  
 Wenn **Sie SQLSetStmtAttr** mit *fOption* auf SQL_ATTR_QUERY_TIMEOUT wird ein Abfragetimeoutintervall festgelegt, um den Server und den Benutzer vor lang andauernden Abfragen zu schützen.  
  
 Das Aufrufen von **SQLSetStmtAttr** mit *fOption,* der auf SQL_ATTR_MAX_LENGTH festgelegt ist, begrenzt die Menge an **Text-** und **Bilddaten,** die eine einzelne Anweisung abrufen kann. Das Aufrufen von **SQLSetStmtAttr** mit *fOption* auf SQL_ATTR_MAX_ROWS beschränkt ein Rowset auch auf die ersten *n* Zeilen, wenn dies alles ist, was die Anwendung erfordert. Beachten Sie, dass das Festlegen von SQL_ATTR_MAX_ROWS bewirkt, dass der Treiber eine SET ROWCOUNT-Anweisung an den Server ausgibt. Dies [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wirkt sich auf alle Anweisungen aus, einschließlich Trigger und Aktualisierungen.  
  
 Gehen Sie beim Festlegen dieser Optionen vorsichtig vor. Im Idealfall sollten alle Anweisungshandle eines Verbindungshandles die gleichen Einstellungen für SQL_ATTR_MAX_LENGTH und SQL_ATTR_MAX_ROWS aufweisen. Wenn der Treiber von einem Anweisungshandle zu einem anderen mit abweichenden Werten für diese Optionen wechselt, muss der Treiber die entsprechenden SET TEXTSIZE- und SET ROWCOUNT-Anweisungen generieren, um die Einstellungen zu ändern. Der Treiber kann diese Anweisungen nicht dem gleichen Batch zuordnen, in dem sich auch die SQL-Anweisung des Benutzers befindet, da die SQL-Anweisung des Benutzers eine Anweisung enthalten kann, die die erste Anweisung in einem Batch darstellen muss. Der Treiber muss die Anweisungen SET TEXTSIZE und SET ROWCOUNT in einem separaten Batch senden, der automatisch einen zusätzlichen Roundtrip zum Server generiert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen von Abfragen &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
