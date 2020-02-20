---
title: Methode „supportsLimitedOuterJoins“ (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsLimitedOuterJoins
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 06225a1a-a58d-4bff-b2ef-be303f051644
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e8e1b235a8c779c652a8678802bbb91a1de83f38
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67969302"
---
# <a name="supportslimitedouterjoins-method-sqlserverdatabasemetadata"></a>supportsLimitedOuterJoins-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ab, ob äußere Joins von dieser Datenbank in eingeschränktem Maß unterstützt werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean supportsLimitedOuterJoins()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** unterstützt. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese supportsLimitedOuterJoins-Methode wird von der supportsLimitedOuterJoins-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
