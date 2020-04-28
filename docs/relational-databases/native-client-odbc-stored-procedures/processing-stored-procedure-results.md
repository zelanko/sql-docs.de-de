---
title: Verarbeiten der Ergebnisse der gespeicherten Prozedur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- stored procedures [ODBC], results
ms.assetid: 788ef2a4-17de-4526-960b-46bf29aafc9f
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d246756161e129f3f1d4c6efe5192ce39ff777d0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304537"
---
# <a name="processing-stored-procedure-results"></a>Verarbeiten von Ergebnissen gespeicherter Prozeduren
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Gespeicherte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Prozeduren verfügen über vier Mechanismen für die Rückgabe von Daten:  
  
-   Jede SELECT-Anweisung in der Prozedur generiert ein Resultset.  
  
-   Die Prozedur kann Daten über Ausgabeparameter zurückgeben.  
  
-   Ein Cursorausgabeparameter kann einen [!INCLUDE[tsql](../../includes/tsql-md.md)]-Servercursor zurück übergeben.  
  
-   Die Prozedur kann einen ganzzahligen Rückgabecode besitzen.  
  
 Anwendungen müssen alle diese Ausgaben gespeicherter Prozeduren verarbeiten können. Die CALL-Anweisung bzw. die EXECUTE-Anweisung sollte Parametermarkierungen für den Rückgabecode und die Ausgabeparameter enthalten. Verwenden Sie [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md) , um alle als Ausgabeparameter zu binden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , und der Native Client-ODBC-Treiber überträgt die Ausgabewerte in die gebundenen Variablen. Ausgabeparameter und Rückgabecodes sind die letzten Elemente, die an den Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zurückgegeben werden. Sie werden erst dann an die Anwendung zurückgegeben, wenn [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md) SQL_NO_DATA zurückgibt.  
  
 ODBC unterstützt das Binden von [!INCLUDE[tsql](../../includes/tsql-md.md)]-Cursorparametern nicht. Da alle Ausgabeparameter vor der Ausführung einer Prozedur gebunden werden müssen, können gespeicherte [!INCLUDE[tsql](../../includes/tsql-md.md)]-Prozeduren, die einen Ausgabecursorparameter enthalten, nicht von ODBC-Anwendungen aufgerufen werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen gespeicherter Prozeduren](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  
