---
title: prepareStatement-Methode (java.lang.String, int, int, int) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.prepareStatement (java.lang.String, int, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b78d2192-f315-4c45-9051-c77059e2c3f4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4a47ac1202ec73c15198b9b6f3c87ee53e027c83
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67976182"
---
# <a name="preparestatement-method-javalangstring-int-int-int"></a>prepareStatement-Methode (java.lang.String, int, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Erstellt ein [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)-Objekt, mit dem [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekte mit dem angegebenen Typ sowie der Parallelität und Haltbarkeit generiert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.PreparedStatement prepareStatement(java.lang.String sql,  
                                                   int nType,  
                                                   int nConcur,  
                                                   int nHold)  
```  
  
#### <a name="parameters"></a>Parameter  
 *sql*  
  
 Eine **Zeichenfolge**, die eine SQL-Anweisung enthält.  
  
 *nType*  
  
 Ein Wert vom Typ **int** zur Angabe des Resultsettyps.  
  
 *nConcur*  
  
 Ein Wert vom Typ **int** zur Angabe des Parallelitätstyps des Resultsets.  
  
 *nHold*  
  
 Ein Wert vom Typ **int** zum Angeben der Resultsethaltbarkeit.  
  
## <a name="return-value"></a>Rückgabewert  
 Dies ist ein PreparedStatement-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese prepareStatement-Methode wird von der prepareStatement-Methode in der java.sql.Connection-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [prepareStatement-Methode &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/preparestatement-method-sqlserverconnection.md)   
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
