---
title: createStatement(int, int, int)-Methode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.createStatement (int, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2e4fa385-8f61-4394-8f75-3e839930a57d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 74cc1b97c121b5e1a6e7d55127ec18cd2caec4fd
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67955359"
---
# <a name="createstatement-method-int-int-int"></a>createStatement-Methode (int, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Erstellt ein [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt, mit dem [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekte mit dem angegebenen Typ sowie der Parallelität und Haltbarkeit generiert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.Statement createStatement(int nType,  
                                          int nConcur,  
                                          int nHold)  
```  
  
#### <a name="parameters"></a>Parameter  
 *resultSetType*  
  
 Der Wert vom Typ **int**, der den Resultsettyp darstellt.  
  
 *nConcur*  
  
 Der Wert vom Typ **int**, der den Resultset-Parallelitätstyp darstellt.  
  
 *nHold*  
  
 Der Wert vom Typ **int**, der die Haltbarkeit darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Das Statement-Objekt  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese createStatement-Methode wird von der createStatement-Methode in der java.sql.Connection-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [createStatement-Methode &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md)   
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
