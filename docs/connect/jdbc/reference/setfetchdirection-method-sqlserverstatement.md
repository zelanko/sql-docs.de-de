---
title: setFetchDirection-Methode (SQLServerStatement) | Microsoft-Dokumentation
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
ms.openlocfilehash: 995f3f0f63728d397cf51013bd5429943e9cac0c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67974394"
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
 Diese setFetchDirection-Methode wird von der setFetchDirection-Methode in der Java. SQL. Statement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerStatement-Elemente](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement-Klasse](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
