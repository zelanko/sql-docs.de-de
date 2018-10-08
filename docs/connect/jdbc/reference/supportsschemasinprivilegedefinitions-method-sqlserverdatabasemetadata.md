---
title: SupportsSchemasInPrivilegeDefinitions-Methode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsSchemasInPrivilegeDefinitions
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2957af1d-62d6-4375-b214-bbba9aafcc2d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e2c669d27df0762ee66e37c7fee7be03c0c0d1d1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47694964"
---
# <a name="supportsschemasinprivilegedefinitions-method-sqlserverdatabasemetadata"></a>supportsSchemasInPrivilegeDefinitions-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ab, ob in einer Berechtigungsdefinitionsanweisung ein Schemaname verwendet werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean supportsSchemasInPrivilegeDefinitions()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** unterstützt. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese SupportsSchemasInPrivilegeDefinitions-Methode wird von der SupportsSchemasInPrivilegeDefinitions-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
