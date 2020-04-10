---
title: getURL-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getURL
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: fcb66851-db5f-4ae8-b728-d129480b6f42
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 526eb87409eaf08c8947e1a85c4e4ef68247daff
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80910626"
---
# <a name="geturl-method-sqlserverdatabasemetadata"></a>getURL-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft die URL für diese Datenbank ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.lang.String getURL()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **String-Objekt**, das die URL enthält.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getURL-Methode wird von der getURL-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
 Wird [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] mit einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank verwendet, gibt diese Methode einen **String-Wert** zurück, der die folgenden Informationen enthält:  
  
-   URL-Wert "jdbc:sqlserver://"  
  
-   optionale Verbindungseigenschaften wie **serverName**, **instanceName** und **portNumber**  
  
-   Andere, vom Benutzer festgelegte Verbindungseigenschaften sowie alle Verbindungseigenschaften mit Treiberstandardwerten, die nicht leer und nicht NULL sind (mit Ausnahme von **userName**, **password** und **integratedSecurity**)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
