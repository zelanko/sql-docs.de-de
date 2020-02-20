---
title: getStatement-Methode (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getStatement
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7dea981b-b4fd-4f8d-954f-e686124627e2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c7fca859273c5eff58cde02b98f98699307ff1b4
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67979582"
---
# <a name="getstatement-method-sqlserverresultset"></a>getStatement-Methode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft das [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt ab, von dem dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt erstellt wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.Statement getStatement()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein SQLServerStatement-Objekt  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getStatement-Methode wird von der getStatement-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Wird das Resultset auf andere Art erstellt, z. B. mit einer [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)-Methode, wird von der Methode NULL zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
