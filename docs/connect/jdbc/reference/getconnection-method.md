---
title: getConnection()-Methode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getConnection ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7f520e96-5313-468f-b987-535ddaea027e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 714ba26610aa27fbc05cb27156b293c13e58130d
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923331"
---
# <a name="getconnection-method-"></a>getConnection-Methode ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Stellt eine Verbindung mit der Datenquelle her, für die dieses [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)-Objekt steht.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.Connection getConnection()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 java.sql.SQLException  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getConnection-Methode wird von der getConnection-Methode in der javax.sql.DataSource-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [getConnection-Methode &#40;SQLServerDataSource&#41;](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md)   
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
