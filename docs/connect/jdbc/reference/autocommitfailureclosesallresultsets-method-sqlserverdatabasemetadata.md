---
title: Schließt der JDBC-Treiber offene Resultsets | Microsoft-Dokumentation
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
ms.openlocfilehash: 9fded722f558b68e393fc4e0815a35cc7383b8d6
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67955857"
---
# <a name="autocommitfailureclosesallresultsets-method-sqlserverdatabasemetadata"></a>autoCommitFailureClosesAllResultSets-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt an, ob vom JDBC-Treiber alle geöffneten Resultsets (einschließlich Resultsets mit Haltbarkeit) geschlossen werden, wenn ein automatischer Commit aktiviert und eine Ausnahme ausgelöst wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean autoCommitFailureClosesAllResultSets()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Der Wert **TRUE** wird zurückgegeben, wenn alle offenen Resultsets, einschließlich der Resultset, die beibehalten werden können, geschlossen werden, wenn der Autocommitmodus aktiviert ist und eine Ausnahme ausgelöst wird. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese autoCommitFailureClosesAllResultSets-Methode wird von der autoCommitFailureClosesAllResultSets-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
