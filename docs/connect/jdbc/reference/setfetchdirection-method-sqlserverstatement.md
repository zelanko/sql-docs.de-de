---
title: SetFetchDirection-Methode (SQLServerStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.setFetchDirection
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 18176517-2fb3-4266-924d-0f01253083d2
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: a23f058eea5512181bdbea277c4bccc6d1ff2616
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66803387"
---
# <a name="setfetchdirection-method-sqlserverstatement"></a>setFetchDirection-Methode (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt für [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] die Richtung an, in der die Resultsetzeilen verarbeitet werden sollen.  
  
> [!NOTE]  
>  Die Angabe dieser Methode wird vom JDBC-Treiber derzeit ignoriert.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final void setFetchDirection(int nDir)  
```  
  
#### <a name="parameters"></a>Parameter  
 *nDir*  
  
 Ein Wert vom Typ **int** zum Angeben der Zeilenverarbeitungsrichtung. Mögliche Werte:  
  
 FETCH_FORWARD  
  
 FETCH_REVERSE  
  
 FETCH_UNKNOWN  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese SetFetchDirection-Methode wird von der SetFetchDirection-Methode in der java.sql.Statement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerStatement-Elemente](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement-Klasse](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
