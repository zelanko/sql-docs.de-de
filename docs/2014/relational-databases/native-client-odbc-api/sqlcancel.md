---
title: SQLCancel | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLCancel function
ms.assetid: d4c965ae-c1ac-4e9d-b4b9-32b561401106
caps.latest.revision: 5
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6aff7aea0040e2fd7f86a3ad668b4e4438148497
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36160905"
---
# <a name="sqlcancel"></a>SQLCancel
  Die [SQLCancel](http://go.microsoft.com/fwlink/?LinkId=203516) Thema besagt, dass in ODBC 2.x, wenn eine Anwendung ruft `SQLCancel` Wenn bei der Anweisung, keine Verarbeitung erfolgt `SQLCancel` hat dieselbe Wirkung wie das `SQLFreeStmt` mit der `SQL_CLOSE` Option; diese das Verhalten wird nur der Vollständigkeit halber definiert und Anwendungen sollten Aufrufen `SQLFreeStmt` oder `SQLCloseCursor` um Cursor zu schließen. Aber auch wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-Anwendung die ODBC API-Version auf 3.5.x oder höher festlegt, verwendet die `SQLCancel`-Funktion das ODBC 2.x-Verhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [SQLCancel](http://go.microsoft.com/fwlink/?LinkId=203516)   
 [ODBC-API-Implementierungsdetails](odbc-api-implementation-details.md)  
  
  