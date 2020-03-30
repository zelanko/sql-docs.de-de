---
title: getWarnings-Methode (SQLServerStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getWarnings
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3d6decae-2570-4ca5-8ff6-57a2cc3e921f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3bdb05e7d538de461596e1e7bc4b2db715825fae
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67978064"
---
# <a name="getwarnings-method-sqlserverstatement"></a>getWarnings-Methode (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft die erste Warnung ab, die von Aufrufen für dieses [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt gemeldet wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final java.sql.SQLWarning getWarnings()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein SQLWarning-Objekt  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getWarnings-Methode wird von der getWarnings-Methode in der java.sql.Statement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerStatement-Elemente](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement-Klasse](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
