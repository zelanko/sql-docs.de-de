---
title: rowUpdated-Methode (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.rowUpdated
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 29303550-294e-4d43-b892-312b42e21271
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9eb0f1bf73f719550ce0a00b3b7f96fab9c2af38
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67975660"
---
# <a name="rowupdated-method-sqlserverresultset"></a>rowUpdated-Methode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ab, ob die aktuelle Zeile aktualisiert wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean rowUpdated()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **true** , wenn beide Zeilen vom Besitzer oder einem anderen Benutzer sichtbar aktualisiert wurden und Updates erkannt werden. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese rowaktualisierte-Methode wird von der rowaktualisierte-Methode in der Java. SQL. Resultset-Schnittstelle angegeben.  
  
 Der zurückgegebene Wert ist davon abhängig, ob vom Resultset Updates ermittelt werden.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ermittelt für Cursortypen keine aktualisierten Zeilen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
