---
title: supportsOuterJoins-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsOuterJoins
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9dd19257-b120-4b74-8055-6570a343fc8d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e79d93030bc8bafbc569e8bbcd289479c760750e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67969038"
---
# <a name="supportsouterjoins-method-sqlserverdatabasemetadata"></a>supportsOuterJoins-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ab, ob von dieser Datenbank eine Form von äußeren Joins unterstützt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean supportsOuterJoins()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** unterstützt. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese supportsOuterJoins-Methode wird von der supportsOuterJoins-Methode in der Java. SQL. DatabaseMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
