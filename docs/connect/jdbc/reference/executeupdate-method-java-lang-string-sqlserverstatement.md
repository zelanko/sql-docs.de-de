---
title: executeUpdate-Methode (java.lang.String) (SQLServerStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.executeUpdate (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 85e7c3a2-f2da-49bf-9d90-5fd246fd60e1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6432cd0d09dac50857a0bd1da16a3ded92bb09c5
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80924257"
---
# <a name="executeupdate-method-javalangstring-sqlserverstatement"></a>executeUpdate-Methode (java.lang.String) (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Führt die angegebene SQL-Anweisung aus. Hierbei kann es sich um eine Anweisung vom Typ "INSERT", "UPDATE" oder "DELETE" oder um eine SQL-Anweisung handeln, von der nichts zurückgegeben wird (beispielsweise eine SQL-DDL-Anweisung). Ab dem JDBC-Treiber 3.0 für [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] wird von executeUpdate die richtige Anzahl an Zeilen zurückgegeben, die in einem MERGE-Vorgang aktualisiert wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public int executeUpdate(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>Parameter  
 *sql*  
  
 Ein **String-Objekt** mit der SQL-Anweisung.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **int**-Wert, der die Anzahl der betroffenen Zeilen angibt, oder „0“ bei Verwendung einer DDL-Anweisung.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese executeUpdate-Methode wird von der executeUpdate-Methode in der java.sql.Statement-Schnittstelle angegeben.  
  
 Wenn das Ausführen einer gespeicherten Prozedur zu einer Updatezählung größer als 1 führt oder mehrere Resultsets generiert werden, führen Sie die gespeicherte Prozedur mit der [execute](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md)-Methode aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [executeUpdate-Methode &#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md)   
 [SQLServerStatement-Elemente](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement-Klasse](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
