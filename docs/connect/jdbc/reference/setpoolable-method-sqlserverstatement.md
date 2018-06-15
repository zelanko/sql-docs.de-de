---
title: SetPoolable-Methode (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f0f798c8-cafb-4acc-b85d-2e0059c91d92
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1cc4938abaf5c281da0bae0c14d86b85883d4062
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "32844435"
---
# <a name="setpoolable-method-sqlserverstatement"></a>SetPoolable-Methode (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Sendet eine Anforderung, dass dem Pool eine Anweisung hinzugefügt bzw. nicht hinzugefügt werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setPoolable(boolean poolable) throws SQLException  
```  
  
#### <a name="parameters"></a>Parameter  
 *dem Pool hinzugefügt werden*  
  
 Wenn **"true"**, fordert, dass die Anweisung "zusammengelegt" werden. Wenn **"false"**, fordert, dass die Anweisung nicht in einem Pool zusammengefasst werden.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Hinweise  
 Der Wert im angegebenen der *Pool* Parameter ist ein Hinweis für die Anweisung Pool-Implementierung, der angibt, ob die Anwendung die Anweisung "zusammengelegt" werden möchte. Vom Anweisungspoolmanager wird entschieden, ob dieser Hinweis verwendet wird.  
  
 Der Poolwert einer Anwendung gilt für vom Treiber implementierte interne Anweisungscaches und externe von Anwendungsservern oder anderen Anwendungen implementierte Anweisungscaches.  
  
 Standardmäßig ist ein SQLServerStatement-Objekt nicht dem Pool hinzugefügt werden, wenn erstellt. Sqlserverpreparedstatement- und SQLServerCallableStatement-Objekte werden dem Pool hinzugefügt werden, wenn erstellt.  
  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) wird ausgelöst, wenn diese Methode für eine geschlossene Anweisung aufgerufen wird.  
  
 [von IsPoolable](../../../connect/jdbc/reference/ispoolable-method-sqlserverstatement.md) gibt einen Wert, der angibt, ob das Objekt dem Pool hinzugefügt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [SQLServerStatement-Elemente](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement-Klasse](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
