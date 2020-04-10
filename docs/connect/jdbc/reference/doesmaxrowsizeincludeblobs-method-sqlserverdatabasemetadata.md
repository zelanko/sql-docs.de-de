---
title: doesMaxRowSizeIncludeBlobs-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.doesMaxRowSizeIncludeBlobs
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 0c90a7a7-5a59-4858-bb26-3e725d8611d7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 617f30347d61771347788e7f21152506c4b96411
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922155"
---
# <a name="doesmaxrowsizeincludeblobs-method-sqlserverdatabasemetadata"></a>doesMaxRowSizeIncludeBlobs-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ab, ob der Rückgabewert für die [getMaxRowSize](../../../connect/jdbc/reference/getmaxrowsize-method-sqlserverdatabasemetadata.md)-Methode die SQL-Datentypen „LONGVARCHAR“ und „LONGVARBINARY“ beinhaltet.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean doesMaxRowSizeIncludeBlobs()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Der Wert **TRUE** wird zurückgegeben, wenn der Rückgabewert die Datentypen enthält. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese doesMoxRowSizeIncludeBlobs-Methode wird von der doesMoxRowSizeIncludeBlobs-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
