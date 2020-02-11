---
title: Verarbeiten der Ergebnisse der gespeicherten Prozedur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- stored procedures [ODBC], results
ms.assetid: 788ef2a4-17de-4526-960b-46bf29aafc9f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3e7ffe8b73a7df4cbe2fddcaa0864e338b039f53
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68205487"
---
# <a name="processing-stored-procedure-results"></a>Verarbeiten von Ergebnissen gespeicherter Prozeduren
  Gespeicherte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Prozeduren verfügen über vier Mechanismen für die Rückgabe von Daten:  
  
-   Jede SELECT-Anweisung in der Prozedur generiert ein Resultset.  
  
-   Die Prozedur kann Daten über Ausgabeparameter zurückgeben.  
  
-   Ein Cursorausgabeparameter kann einen [!INCLUDE[tsql](../../includes/tsql-md.md)]-Servercursor zurück übergeben.  
  
-   Die Prozedur kann einen ganzzahligen Rückgabecode besitzen.  
  
 Anwendungen müssen alle diese Ausgaben gespeicherter Prozeduren verarbeiten können. Die CALL-Anweisung bzw. die EXECUTE-Anweisung sollte Parametermarkierungen für den Rückgabecode und die Ausgabeparameter enthalten. Verwenden Sie [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) , um alle als Ausgabeparameter zu binden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , und der Native Client-ODBC-Treiber überträgt die Ausgabewerte in die gebundenen Variablen. Ausgabeparameter und Rückgabecodes sind die letzten Elemente, die an den Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zurückgegeben werden. Sie werden erst dann an die Anwendung zurückgegeben, wenn [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) SQL_NO_DATA zurückgibt.  
  
 ODBC unterstützt das Binden von [!INCLUDE[tsql](../../includes/tsql-md.md)]-Cursorparametern nicht. Da alle Ausgabeparameter vor der Ausführung einer Prozedur gebunden werden müssen, können gespeicherte [!INCLUDE[tsql](../../includes/tsql-md.md)]-Prozeduren, die einen Ausgabecursorparameter enthalten, nicht von ODBC-Anwendungen aufgerufen werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen gespeicherter Prozeduren](running-stored-procedures.md)  
  
  
