---
title: allProceduresAreCallable-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.allProceduresAreCallable
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8886137d-455e-497c-afea-4b326eda52f1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 559c025a5fcb7d27f4520cea0868761b449107a9
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67955928"
---
# <a name="allproceduresarecallable-method-sqlserverdatabasemetadata"></a>allProceduresAreCallable-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ab, ob der aktuelle Benutzer zum Aufrufen aller Prozeduren berechtigt ist, die von der [getProcedures](../../../connect/jdbc/reference/getprocedures-method-sqlserverdatabasemetadata.md)-Methode zurückgegeben werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean allProceduresAreCallable()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Der Wert **TRUE** wird zurückgegeben, wenn der Benutzer über Berechtigungen zum Aufrufen aller Prozeduren verfügt. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese allProceduresAreCallable-Methode wird von der allProceduresAreCallable-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
