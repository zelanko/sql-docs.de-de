---
title: getMaxProcedureNameLength-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getMaxProcedureNameLength
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e1c05eb3-8465-46fd-99bc-5e8effcafee5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 21cfb0df256208522a7e32881352fa000799070a
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80906856"
---
# <a name="getmaxprocedurenamelength-method-sqlserverdatabasemetadata"></a>getMaxProcedureNameLength-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft die maximale Anzahl von Zeichen ab, die bei dieser Datenbank für einen Prozedurnamen zulässig sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public int getMaxProcedureNameLength()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert vom Typ **int** zum Angeben der maximalen Anzahl der zulässigen Zeichen.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getMaxProcedureNameLength-Methode wird von der getMaxProcedureNameLength-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
