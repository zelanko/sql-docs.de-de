---
title: SupportsNonNullableColumns-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsNonNullableColumns
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7c32ea64-460e-4636-8a3b-07c8abeed687
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 3c3e8267ed8a56313b204c127f3712efcbea8d8e
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66796775"
---
# <a name="supportsnonnullablecolumns-method-sqlserverdatabasemetadata"></a>supportsNonNullableColumns-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ab, ob Spalten in dieser Datenbank als Spalten definiert werden können, in denen keine NULL-Werte zulässig sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean supportsNonNullableColumns()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** unterstützt. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese SupportsNonNullableColumns-Methode wird von der SupportsNonNullableColumns-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
