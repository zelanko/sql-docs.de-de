---
title: isFirst-Methode (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.isFirst
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2ff94b95-32ad-4378-8bb1-970030527bb2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b847361621ad8d44840aa4bab02e4877128e8f48
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67977623"
---
# <a name="isfirst-method-sqlserverresultset"></a>isFirst-Methode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ab, ob sich der Cursor in der ersten Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts befindet.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean isFirst()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **TRUE**, wenn sich der Cursor in der ersten Zeile befindet. Der Wert **FALSE** wird zurückgegeben, wenn sich der Cursor an einer beliebigen anderen Position befindet oder wenn das Resultset keine Zeilen enthält.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese isFirst-Methode wird von der isFirst-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Wird diese Methode mit Vorwärtscursors und dynamischen Cursors verwendet, wird eine Ausnahme ausgelöst.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
