---
title: RowUpdated-Methode (SQLServerResultSet) | Microsoft-Dokumentation
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
manager: jroth
ms.openlocfilehash: b827ebb9740c9d88017c5d47626b9a1cef493143
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66765268"
---
# <a name="rowupdated-method-sqlserverresultset"></a>rowUpdated-Methode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ab, ob die aktuelle Zeile aktualisiert wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean rowUpdated()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** Wenn sowohl die Zeile sichtbar vom Besitzer oder von einem anderen Benutzer aktualisiert wurde, und Updates erkannt werden. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese RowUpdated-Methode wird von der Rowudated-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Der zurückgegebene Wert ist davon abhängig, ob vom Resultset Updates ermittelt werden.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ermittelt für Cursortypen keine aktualisierten Zeilen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
