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
manager: craigg
ms.openlocfilehash: 40afdf8854e40050e718b9c456eaf0a41f7430b4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47614926"
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
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
