---
title: SQLCancel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLCancel function
ms.assetid: d4c965ae-c1ac-4e9d-b4b9-32b561401106
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ed3bdb4cc5c2508435bff011545b5b9113d7aeac
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37424389"
---
# <a name="sqlcancel"></a>SQLCancel
  Die [SQLCancel](http://go.microsoft.com/fwlink/?LinkId=203516) Thema angegeben, dass in ODBC 2.x, wenn eine Anwendung ruft `SQLCancel` Wenn in der Anweisung keine Verarbeitung erfolgt `SQLCancel` hat dieselbe Wirkung wie das `SQLFreeStmt` mit der `SQL_CLOSE` Option; dies das Verhalten wird nur der Vollständigkeit halber definiert, und Anwendungen sollten Aufrufen `SQLFreeStmt` oder `SQLCloseCursor` um Cursor zu schließen. Aber auch wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-Anwendung die ODBC API-Version auf 3.5.x oder höher festlegt, verwendet die `SQLCancel`-Funktion das ODBC 2.x-Verhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [SQLCancel](http://go.microsoft.com/fwlink/?LinkId=203516)   
 [ODBC-API-Implementierungsdetails](odbc-api-implementation-details.md)  
  
  
