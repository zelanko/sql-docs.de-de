---
title: Verarbeiten von Ergebnissen für gespeicherte Prozeduren | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- stored procedures [ODBC], results
ms.assetid: 788ef2a4-17de-4526-960b-46bf29aafc9f
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cfc9756a6c55e4ff894b56ec483e921a1acb6b68
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049197"
---
# <a name="processing-stored-procedure-results"></a>Verarbeiten von Ergebnissen gespeicherter Prozeduren
  Gespeicherte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Prozeduren verfügen über vier Mechanismen für die Rückgabe von Daten:  
  
-   Jede SELECT-Anweisung in der Prozedur generiert ein Resultset.  
  
-   Die Prozedur kann Daten über Ausgabeparameter zurückgeben.  
  
-   Ein Cursorausgabeparameter kann einen [!INCLUDE[tsql](../../includes/tsql-md.md)]-Servercursor zurück übergeben.  
  
-   Die Prozedur kann einen ganzzahligen Rückgabecode besitzen.  
  
 Anwendungen müssen alle diese Ausgaben gespeicherter Prozeduren verarbeiten können. Die CALL-Anweisung bzw. die EXECUTE-Anweisung sollte Parametermarkierungen für den Rückgabecode und die Ausgabeparameter enthalten. Verwendung [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) sie alle als Ausgabeparameter zu binden und die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber überträgt die Ausgabewerte an die gebundenen Variablen. Ausgabeparameter und Rückgabecodes werden die letzten Elemente zurückgegeben, die an den Client von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; sie werden nicht zurückgegeben, an die Anwendung bis [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) gibt SQL_NO_DATA zurück.  
  
 ODBC unterstützt das Binden von [!INCLUDE[tsql](../../includes/tsql-md.md)]-Cursorparametern nicht. Da alle Ausgabeparameter vor der Ausführung einer Prozedur gebunden werden müssen, können gespeicherte [!INCLUDE[tsql](../../includes/tsql-md.md)]-Prozeduren, die einen Ausgabecursorparameter enthalten, nicht von ODBC-Anwendungen aufgerufen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen gespeicherter Prozeduren](running-stored-procedures.md)  
  
  