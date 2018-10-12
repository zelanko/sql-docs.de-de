---
title: prepareStatement-Methode (java.lang.String, int, int) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.prepareStatement (java.lang.String, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5bb96dbe-f673-41b5-911b-8f661cca071a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 95c3f823e230a51ada0f966c68a71b189eb482d2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47812388"
---
# <a name="preparestatement-method-javalangstring-int-int"></a>prepareStatement-Methode (java.lang.String, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Erstellt ein [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)-Objekt, mit dem [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekte mit dem angegebenen Typ und der Parallelität generiert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.PreparedStatement prepareStatement(java.lang.String sSql,  
                                                   int resultSetType,  
                                                   int resultSetConcurrency)  
```  
  
#### <a name="parameters"></a>Parameter  
 *SQL*  
  
 Eine **Zeichenfolge**, die eine SQL-Anweisung enthält.  
  
 *resultSetType*  
  
 Ein Wert vom Typ **int** zur Angabe des Resultsettyps.  
  
 *resultSetConcurrency*  
  
 Ein Wert vom Typ **int** zur Angabe des Parallelitätstyps des Resultsets.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein "PreparedStatement"-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese PrepareStatement-Methode wird von der PrepareStatement-Methode in der java.sql.Connection-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerConnection-Methoden](../../../connect/jdbc/reference/sqlserverconnection-methods.md)   
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
