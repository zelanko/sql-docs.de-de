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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 18ffd4adb4387d8b7bc4209cd8e8532abdd686ac
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82709545"
---
# <a name="processing-stored-procedure-results"></a>Verarbeiten von Ergebnissen gespeicherter Prozeduren
  Gespeicherte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Prozeduren verfügen über vier Mechanismen für die Rückgabe von Daten:  
  
-   Jede SELECT-Anweisung in der Prozedur generiert ein Resultset.  
  
-   Die Prozedur kann Daten über Ausgabeparameter zurückgeben.  
  
-   Ein Cursorausgabeparameter kann einen [!INCLUDE[tsql](../../includes/tsql-md.md)]-Servercursor zurück übergeben.  
  
-   Die Prozedur kann einen ganzzahligen Rückgabecode besitzen.  
  
 Anwendungen müssen alle diese Ausgaben gespeicherter Prozeduren verarbeiten können. Die CALL-Anweisung bzw. die EXECUTE-Anweisung sollte Parametermarkierungen für den Rückgabecode und die Ausgabeparameter enthalten. Verwenden Sie [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) , um alle als Ausgabeparameter zu binden, und der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber überträgt die Ausgabewerte in die gebundenen Variablen. Ausgabeparameter und Rückgabecodes sind die letzten Elemente, die von an den Client zurückgegeben werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Sie werden erst an die Anwendung zurückgegeben, wenn [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) SQL_NO_DATA zurückgibt.  
  
 ODBC unterstützt das Binden von [!INCLUDE[tsql](../../includes/tsql-md.md)]-Cursorparametern nicht. Da alle Ausgabeparameter vor der Ausführung einer Prozedur gebunden werden müssen, können gespeicherte [!INCLUDE[tsql](../../includes/tsql-md.md)]-Prozeduren, die einen Ausgabecursorparameter enthalten, nicht von ODBC-Anwendungen aufgerufen werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen gespeicherter Prozeduren](running-stored-procedures.md)  
  
  
