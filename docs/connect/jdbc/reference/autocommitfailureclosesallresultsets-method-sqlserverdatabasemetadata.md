---
title: Schließt JDBC-Treiber geöffneten Resultsets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 1739ecb5-e5cb-4807-b5a8-97c0299929d0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d9d123fce60875b975b8b9d19f2586e79f0e5ce5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47736237"
---
# <a name="autocommitfailureclosesallresultsets-method-sqlserverdatabasemetadata"></a>autoCommitFailureClosesAllResultSets-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt an, ob vom JDBC-Treiber alle geöffneten Resultsets (einschließlich Resultsets mit Haltbarkeit) geschlossen werden, wenn ein automatischer Commit aktiviert und eine Ausnahme ausgelöst wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean autoCommitFailureClosesAllResultSets()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** , wenn alle der offenen führen Mengen, einschließlich der holdable, geschlossen werden, wenn ein automatischer Commit aktiviert ist, und es wird eine Ausnahme ausgelöst. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese AutoCommitFailureClosesAllResultSets-Methode wird von der AutoCommitFailureClosesAllResultSets-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
