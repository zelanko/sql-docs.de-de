---
title: isLast-Methode (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.isLast
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 85d4451f-6392-470e-ab21-78a495b45792
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 840d1183794a5d69ad108aef8eee9ef7aedffe4b
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67977613"
---
# <a name="islast-method-sqlserverresultset"></a>isLast-Methode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ab, ob sich der Cursor in der letzten Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts befindet.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean isLast()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Der Wert **TRUE** wird zurückgegeben, wenn der Cursor in der letzten Zeile liegt. Der Wert **FALSE** wird zurückgegeben, wenn der Cursor sich an einer beliebigen anderen Position befindet oder wenn das Resultset keine Zeilen enthält.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese isLast-Methode wird von der isLast-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Wird diese Methode mit Vorwärtscursors und dynamischen Cursors verwendet, wird eine Ausnahme ausgelöst.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
