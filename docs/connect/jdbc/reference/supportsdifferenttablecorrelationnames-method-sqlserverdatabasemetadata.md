---
title: supportsDifferentTableCorrelationNames-Methode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsDifferentTableCorrelationNames
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b4f8db0c-2eaf-476b-b916-3e83355778f7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3c938fc0da6ed235f080492e573ad558d75751c2
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67969424"
---
# <a name="supportsdifferenttablecorrelationnames-method-sqlserverdatabasemetadata"></a>supportsDifferentTableCorrelationNames-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ab, ob sich abhängige Tabellennamen (sofern diese unterstützt werden) von den Namen der Tabellen unterscheiden müssen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean supportsDifferentTableCorrelationNames()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** unterstützt. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese supportsDifferentTableCorrelationNames-Methode wird von der supportsDifferentTableCorrelationNames-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
