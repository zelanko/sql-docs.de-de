---
title: Methode „getDefaultTransactionIsolation“ (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getDefaultTransactionIsolation
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 85b867ed-de5a-4879-b3f8-bce897879077
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 58be916063f1bd0893285c6c893241e3ec4e699f
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80917719"
---
# <a name="getdefaulttransactionisolation-method-sqlserverdatabasemetadata"></a>getDefaultTransactionIsolation-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft die standardmäßige Transaktionsisolationsstufe für diese Datenbank ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public int getDefaultTransactionIsolation()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert vom Typ **int** zum Angeben der standardmäßigen verwendeten Transaktionsisolationsstufe.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getDefaultTransactionIsolation-Methode wird von der getDefaultTransactionIsolation-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
 Bei Verwendung von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] mit einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank wird von dieser Methode entweder der Wert TRANSACTION_READ_COMMITTED oder der Wert 2 vom Typ **int** zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
