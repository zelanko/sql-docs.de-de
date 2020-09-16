---
description: getConcurrency-Methode (SQLServerResultSet)
title: getConcurrency-Methode (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getConcurrency
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 207e25f4-769c-4ff3-913c-3517b06208e4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b8cb92a019c9c65e867be023fab9bc299a7a8bc8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88436552"
---
# <a name="getconcurrency-method-sqlserverresultset"></a>getConcurrency-Methode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft den Parallelitätsmodus dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public int getConcurrency()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert vom Typ **int** zum Angeben des Parallelitätstyps. Mögliche Werte:  
  
 ResultSet.CONCUR_READ_ONLY  
  
 ResultSet.CONCUR_UPDATABLE  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getConcurrency-Methode wird von der getConcurrency-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Die verwendete Parallelität wird vom [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt bestimmt, von dem das Resultset erstellt wurde.  
  
 Diese Methode kann zur Bestimmung der eigentlichen Parallelität verwendet werden. Wurde von der Anwendung "CONCUR_READ_ONLY" oder "CONCUR_UPDATABLE" ausgewählt, werden diese Elemente zurückgegeben. Wurde von der Anwendung die Standardparallelität verwendet, wird "CONCUR_READ_ONLY" zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
