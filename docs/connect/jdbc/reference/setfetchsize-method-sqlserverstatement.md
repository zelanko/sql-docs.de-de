---
title: SetFetchSize-Methode (SQLServerStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.setFetchSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 760e555e-9667-4b40-b0ba-778026ff2923
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: acf74ae4b3f9c95002de418a5b77a44a7b0a1bfa
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66764601"
---
# <a name="setfetchsize-method-sqlserverstatement"></a>setFetchSize-Methode (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt für den [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] an, wie viele Zeilen aus der Datenbank abgerufen werden sollen, wenn weitere Zeilen benötigt werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final void setFetchSize(int rows)  
```  
  
#### <a name="parameters"></a>Parameter  
 *rows*  
  
 Ein Wert vom Typ **int**, der die Anzahl der abzurufenden Zeilen angibt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese SetFetchSize-Methode wird von der SetFetchSize-Methode in der java.sql.Statement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerStatement-Elemente](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement-Klasse](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
