---
title: SQLCancel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLCancel function
ms.assetid: d4c965ae-c1ac-4e9d-b4b9-32b561401106
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 816e93c7cf65d622bcd48cbf5a93eb5abba32adb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48077795"
---
# <a name="sqlcancel"></a>SQLCancel
  Die [SQLCancel](http://go.microsoft.com/fwlink/?LinkId=203516) Thema angegeben, dass in ODBC 2.x, wenn eine Anwendung ruft `SQLCancel` Wenn in der Anweisung keine Verarbeitung erfolgt `SQLCancel` hat dieselbe Wirkung wie das `SQLFreeStmt` mit der `SQL_CLOSE` Option; dies das Verhalten wird nur der Vollständigkeit halber definiert, und Anwendungen sollten Aufrufen `SQLFreeStmt` oder `SQLCloseCursor` um Cursor zu schließen. Aber auch wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-Anwendung die ODBC API-Version auf 3.5.x oder höher festlegt, verwendet die `SQLCancel`-Funktion das ODBC 2.x-Verhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [SQLCancel](http://go.microsoft.com/fwlink/?LinkId=203516)   
 [ODBC-API-Implementierungsdetails](odbc-api-implementation-details.md)  
  
  
