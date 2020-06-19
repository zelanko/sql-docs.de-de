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
author: rothja
ms.author: jroth
ms.openlocfilehash: dc3d86229501f80b25fb077788d1835a5f4f5c96
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85022895"
---
# <a name="sqlcancel"></a>SQLCancel
  Das [SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516) -Thema besagt, dass in ODBC 2. x, wenn eine Anwendung aufruft, `SQLCancel` Wenn keine Verarbeitung in der Anweisung ausgeführt wird, `SQLCancel` denselben Effekt hat wie `SQLFreeStmt` bei der `SQL_CLOSE` -Option. dieses Verhalten wird nur aus Gründen der Vollständigkeit definiert, und Anwendungen sollten `SQLFreeStmt` oder aufrufen `SQLCloseCursor` , um Cursor zu schließen. Aber auch wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-Anwendung die ODBC API-Version auf 3.5.x oder höher festlegt, verwendet die `SQLCancel`-Funktion das ODBC 2.x-Verhalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
