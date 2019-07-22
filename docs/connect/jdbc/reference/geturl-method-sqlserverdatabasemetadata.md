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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4aa608851ddbe00c8d7c09523c0f3b8f9ec95ff6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67978212"
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
  
## <a name="remarks"></a>Remarks  
 Diese getURL-Methode wird von der getURL-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
 Wird [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] mit einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank verwendet, gibt diese Methode einen **String-Wert** zurück, der die folgenden Informationen enthält:  
  
-   URL-Wert "jdbc:sqlserver://"  
  
-   Optionale Verbindungs Eigenschaften, z. b. **Servername**, **instanceName**und **PortNumber**  
  
-   Andere, vom Benutzer festgelegte Verbindungseigenschaften sowie alle Verbindungseigenschaften mit Treiberstandardwerten, die nicht leer und nicht NULL sind (mit Ausnahme von **userName**, **password** und **integratedSecurity**)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
