---
title: SQLEndTran | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLEndTran function
ms.assetid: 95cff841-c2d5-4e1e-a18d-f3d4696a5b85
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f5425fdc189febd23e9fc61765f4ad56fe484111
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63067590"
---
# <a name="sqlendtran"></a>SQLEndTran
  In der Standardeinstellung schließt der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber den mit einer Anweisung verknüpften Cursor, wenn **SQLEndTran** für einen Vorgang ein Commit oder Rollback ausführt. Servercursor werden nicht geschlossen, wenn sie statisch sind. Wenn **SQLEndTran** für einen Vorgang ein Commit oder Rollback ausführt, wird das Verhalten des mit der Anweisung verknüpften Cursors vom Wert des treiberspezifischen ODBC-Verbindungsattributs SQL_COPT_SS_PRESERVE_CURSORS bestimmt, das von [SQLSetConnectAttr](sqlsetconnectattr.md)festgelegt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Implementierungsdetails](odbc-api-implementation-details.md)   
 [SQLEndTran-Funktion](https://go.microsoft.com/fwlink/?LinkId=59342)  
  
  
