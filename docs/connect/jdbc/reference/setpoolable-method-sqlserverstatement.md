---
title: SetPoolable-Methode (SQLServerStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f0f798c8-cafb-4acc-b85d-2e0059c91d92
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 809e16fce7cac83b6ba09fcef676c8da920b0dc3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47759678"
---
# <a name="setpoolable-method-sqlserverstatement"></a>setPoolable-Methode (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Sendet eine Anforderung, dass dem Pool eine Anweisung hinzugefügt bzw. nicht hinzugefügt werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setPoolable(boolean poolable) throws SQLException  
```  
  
#### <a name="parameters"></a>Parameter  
 *dem Pool hinzugefügt werden*  
  
 Wenn der Wert **true** ist, wird angefordert, dass dem Pool die Anweisung hinzugefügt werden soll. Wenn der Wert **false** ist, wird angefordert, dass dem Pool die Anweisung nicht hinzugefügt werden soll.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Der im *poolable*-Parameter angegebene Wert zeigt an, ob die Anweisung dem Pool hinzugefügt werden soll. Vom Anweisungspoolmanager wird entschieden, ob dieser Hinweis verwendet wird.  
  
 Der Poolwert einer Anwendung gilt für vom Treiber implementierte interne Anweisungscaches und externe von Anwendungsservern oder anderen Anwendungen implementierte Anweisungscaches.  
  
 Standardmäßig ist ein SQLServerStatement-Objekt nicht dem Pool hinzugefügt werden, wenn erstellt. Sqlserverpreparedstatement- und SQLServerCallableStatement-Objekte werden dem Pool hinzugefügt werden, wenn erstellt.  
  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) wird ausgelöst, wenn diese Methode in einer geschlossenen-Anweisung aufgerufen wird.  
  
 Von [isPoolable](../../../connect/jdbc/reference/ispoolable-method-sqlserverstatement.md) wird ein Wert zurückgegeben, der anzeigt, ob das Objekt dem Pool hinzugefügt werden kann.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerStatement-Elemente](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement-Klasse](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
