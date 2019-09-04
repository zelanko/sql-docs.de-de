---
title: supportsaltertablewithdropcolumn-Methode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsAlterTableWithDropColumn
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 55a182c1-28e5-4d32-aeb1-166a8ac76758
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0917642d2b3ea166ab3b16144dccd58fa34bbe31
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67969855"
---
# <a name="supportsaltertablewithdropcolumn-method-sqlserverdatabasemetadata"></a>supportsAlterTableWithDropColumn-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ab, ob von dieser Datenbank "ALTER TABLE" mit "drop column" unterstützt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean supportsAlterTableWithDropColumn()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** unterstützt. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese supportsaltertablewithdropcolumn-Methode wird von der supportsaltertablewithdropcolumn-Methode in der Java. SQL. DatabaseMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
