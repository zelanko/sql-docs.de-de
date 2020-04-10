---
title: setPoolable-Methode (SQLServerStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f0f798c8-cafb-4acc-b85d-2e0059c91d92
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8651644bbf67f70642385b8c9b4bd2925dfce5a6
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920757"
---
# <a name="setpoolable-method-sqlserverstatement"></a>setPoolable-Methode (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Sendet eine Anforderung, dass dem Pool eine Anweisung hinzugefügt bzw. nicht hinzugefügt werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setPoolable(boolean poolable) throws SQLException  
```  
  
#### <a name="parameters"></a>Parameter  
 *poolable*  
  
 Wenn der Wert **true** ist, wird angefordert, dass dem Pool die Anweisung hinzugefügt werden soll. Wenn der Wert **false** ist, wird angefordert, dass dem Pool die Anweisung nicht hinzugefügt werden soll.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Der im *poolable*-Parameter angegebene Wert zeigt an, ob die Anweisung dem Pool hinzugefügt werden soll. Vom Anweisungspoolmanager wird entschieden, ob dieser Hinweis verwendet wird.  
  
 Der Poolwert einer Anwendung gilt für vom Treiber implementierte interne Anweisungscaches und externe von Anwendungsservern oder anderen Anwendungen implementierte Anweisungscaches.  
  
 SQLServerStatement-Objekte können standardmäßig nicht bei der Erstellung einem Pool zugewiesen werden. Die Objekte SQLServerPreparedStatement und SQLServerCallableStatement können bei der Erstellung einem Pool zugewiesen werden.  
  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) wird ausgelöst, wenn diese Methode in einer geschlossenen Anweisung aufgerufen wird.  
  
 Von [isPoolable](../../../connect/jdbc/reference/ispoolable-method-sqlserverstatement.md) wird ein Wert zurückgegeben, der anzeigt, ob das Objekt dem Pool hinzugefügt werden kann.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerStatement-Elemente](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement-Klasse](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
