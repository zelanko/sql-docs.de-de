---
title: supportsMultipleOpenResults-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsMultipleOpenResults
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9480d280-5e3d-46ae-80e6-1bba3ac5a641
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 73eab48ff558a5a93eb64b3a9a908914003b579e
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67969267"
---
# <a name="supportsmultipleopenresults-method-sqlserverdatabasemetadata"></a>supportsMultipleOpenResults-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ab, ob von einem [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt gleichzeitig mehrere [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)-Objekte zurückgegeben werden können.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean supportsMultipleOpenResults()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** unterstützt. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese supportsMultipleOpenResults-Methode wird von der supportsMultipleOpenResults-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
