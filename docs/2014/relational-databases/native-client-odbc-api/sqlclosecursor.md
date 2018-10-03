---
title: SQLCloseCursor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLCloseCursor function
ms.assetid: e7134d65-5c1c-4ae2-b119-d9b4b9a42483
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 26b00c4781624bf653ad9a8200a219951dc793c7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48097160"
---
# <a name="sqlclosecursor"></a>SQLCloseCursor
  **SQLCloseCursor** ersetzt [SQLFreeStmt](sqlfreestmt.md) mit einer *Option* von SQL_CLOSE. Beim Empfang von **SQLCloseCursor**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber verwirft ausstehende Resultsetzeilen. Beachten Sie, dass die Spalten- und Parameterbindungen der Anweisung (sofern vorhanden) von **SQLCloseCursor**nicht geändert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [SQLCloseCursor](http://go.microsoft.com/fwlink/?LinkId=59331)   
 [ODBC-API-Implementierungsdetails](odbc-api-implementation-details.md)  
  
  
