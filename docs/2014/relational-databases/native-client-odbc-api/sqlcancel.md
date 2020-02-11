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
ms.openlocfilehash: 8bad2cc35a30f5c6f5855292ff73635cef6072b2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63067837"
---
# <a name="sqlcancel"></a>SQLCancel
  Das [SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516) -Thema besagt, dass in ODBC 2. x, wenn eine `SQLCancel` Anwendung aufruft, wenn keine Verarbeitung für die-Anweisung `SQLCancel` ausgeführt wird, denselben Effekt `SQLFreeStmt` wie bei `SQL_CLOSE` der-Option hat. Dieses Verhalten wird nur aus Gründen der Vollständigkeit definiert, und `SQLFreeStmt` Anwendungen `SQLCloseCursor` sollten oder zum Schließen von Cursorn aufruft. Aber auch wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-Anwendung die ODBC API-Version auf 3.5.x oder höher festlegt, verwendet die `SQLCancel`-Funktion das ODBC 2.x-Verhalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
