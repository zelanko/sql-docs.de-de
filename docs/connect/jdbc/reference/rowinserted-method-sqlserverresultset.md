---
title: RowInserted-Methode (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.rowInserted
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e7c10372-0be8-4baa-87f7-ed6b66003357
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1cdfce0c8ea71eb28c15810bb34a4f39530c0d51
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47616888"
---
# <a name="rowinserted-method-sqlserverresultset"></a>rowInserted-Methode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ab, ob in der aktuellen Zeile eine Einfügung vorgenommen wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean rowInserted()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** Wenn eine Zeile eine Einfügung wurde und einfügungen erkannt werden. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese RowUpdated-Methode wird von der Rowudated-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Der zurückgegebene Wert ist davon abhängig, ob vom [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt sichtbare Einfügungen ermittelt werden können.  
  
> [!NOTE]  
>  Von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] werden für Cursortypen keine eingefügten Zeilen ermittelt.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
