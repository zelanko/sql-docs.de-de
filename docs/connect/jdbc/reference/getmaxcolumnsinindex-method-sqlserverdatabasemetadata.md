---
title: getMaxColumnsInIndex-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getMaxColumnsInIndex
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 108f0e2c-7dc5-4195-8248-0758a75a314e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e32de87add3f02736e877c99ed64c565dc1f6430
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80921270"
---
# <a name="getmaxcolumnsinindex-method-sqlserverdatabasemetadata"></a>getMaxColumnsInIndex-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft die maximale Anzahl von Spalten ab, die bei dieser Datenbank in einem Index zulässig sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public int getMaxColumnsInIndex()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert vom Typ **int** zum Angeben der maximalen Anzahl der zulässigen Spalten.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getMaxColumnsInIndex-Methode wird von der getMaxColumnsInIndex-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
