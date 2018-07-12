---
title: SQLCloseCursor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLCloseCursor function
ms.assetid: e7134d65-5c1c-4ae2-b119-d9b4b9a42483
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1ec1f623d2a770664897fce1247af1c94f506b04
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37425299"
---
# <a name="sqlclosecursor"></a>SQLCloseCursor
  **SQLCloseCursor** ersetzt [SQLFreeStmt](sqlfreestmt.md) mit einer *Option* von SQL_CLOSE. Beim Empfang von **SQLCloseCursor**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber verwirft ausstehende Resultsetzeilen. Beachten Sie, dass die Spalten- und Parameterbindungen der Anweisung (sofern vorhanden) von **SQLCloseCursor**nicht geändert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [SQLCloseCursor](http://go.microsoft.com/fwlink/?LinkId=59331)   
 [ODBC-API-Implementierungsdetails](odbc-api-implementation-details.md)  
  
  
