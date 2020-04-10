---
title: isAfterLast-Methode (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.isAfterLast
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 19f9d124-3184-4985-8b97-503a8ab8b4f9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8542c6a2dc87e1f0d52049b27446acf2c1f909de
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80909856"
---
# <a name="isafterlast-method-sqlserverresultset"></a>isAfterLast-Methode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ab, ob sich der Cursor an einer Position nach der letzten Zeile in diesem [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt befindet.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean isAfterLast()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Der Wert **TRUE** wird zurückgegeben, wenn der Cursor hinter der letzten Zeile liegt. Der Wert **FALSE** wird zurückgegeben, wenn sich der Cursor an einer beliebigen anderen Position befindet oder wenn das Resultset keine Zeilen enthält.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese isAfterLast-Methode wird von der isAfterLast-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Wird diese Methode mit dynamischen Cursors verwendet, einschließlich schreibgeschützten Vorwärtscursors und die selectMethod-Verbindungseigenschaft auf "cursor" festgelegt, wird eine Ausnahme ausgelöst.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
