---
title: supportsOrderByUnrelated-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsOrderByUnrelated
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9ea6c534-8132-49f3-aac3-a12ec4c46df2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5ddbb8fa811a4370db06b4992eb43e26845e1298
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67969072"
---
# <a name="supportsorderbyunrelated-method-sqlserverdatabasemetadata"></a>supportsOrderByUnrelated-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ab, ob von dieser Datenbank die Verwendung einer Spalte, die sich nicht in der SELECT-Anweisung befindet, in einer ORDER BY-Klausel unterstützt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean supportsOrderByUnrelated()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** unterstützt. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese supportsOrderByUnrelated-Methode wird von der supportsOrderByUnrelated-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
