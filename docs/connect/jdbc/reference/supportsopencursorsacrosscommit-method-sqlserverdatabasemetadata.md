---
title: supportsOpenCursorsAcrossCommit-Methode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsOpenCursorsAcrossCommit
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b7eed108-64cc-4be6-b297-8af6c1e3dc72
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 86285b1b0fd7b1b474e549b5046ac1258fdcb3a1
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80912522"
---
# <a name="supportsopencursorsacrosscommit-method-sqlserverdatabasemetadata"></a>supportsOpenCursorsAcrossCommit-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ab, ob von dieser Datenbank unterstützt wird, dass Cursor über Commits hinaus geöffnet bleiben.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean supportsOpenCursorsAcrossCommit()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** unterstützt. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese supportsOpenCursorsAcrossCommit-Methode wird von der supportsOpenCursorsAcrossCommit-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
