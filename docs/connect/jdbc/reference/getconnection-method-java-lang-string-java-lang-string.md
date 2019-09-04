---
title: getConnection-Methode (java.lang.String, java.lang.String) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getConnection (java.lang.String, java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 78db89d6-a8a0-4116-8885-548e627220ed
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 87d3dfc2183bdc00261417a024507b41ea5fde28
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67952744"
---
# <a name="getconnection-method-javalangstring-javalangstring"></a>getConnection-Methode (java.lang.String, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Stellt anhand des Benutzernamens und des Kennworts eine Verbindung mit der Datenquelle her, für die dieses [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)-Objekt steht.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.Connection getConnection(java.lang.String username,  
                                         java.lang.String password)  
```  
  
#### <a name="parameters"></a>Parameter  
 *username*  
  
 Ein **String-Objekt**, das den Benutzernamen enthält.  
  
 *password*  
  
 Eine **Zeichenfolge**, die das Kennwort enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 java.sql.SQLException  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getConnection-Methode wird von der getConnection-Methode in der javax. SQL. DataSource-Schnittstelle angegeben.  
  
 Wenn die getConnection-Methode mit einem Benutzernamen oder Kennwort ungleich NULL aufgerufen wird, werden die Benutzernamen-und Kenn Wort Eigenschaften ersetzt, die für die SQLServerDataSource-Klasse festgelegt werden, wenn das SQLServerConnection-Objekt initialisiert wird. Beispiel: Hat der Aufrufer [setUser](../../../connect/jdbc/reference/setuser-method-sqlserverdatasource.md) und [setPassword](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md) für die Datenquelle aufgerufen und ruft anschließend getConnection auf und gibt einen Benutzernamen und ein Kennwort ungleich NULL an, werden der Benutzername und das Kennwort, der bzw. das durch setUser und setPassword festgelegt sind, durch das an getConnection weitergegebene Kennwort ersetzt.  
  
> [!NOTE]  
>  Benutzernamen und Kennwörter, die in der URL durch einen Aufruf der [setURL](../../../connect/jdbc/reference/seturl-method-sqlserverdatasource.md)-Methode festgelegt sind, werden in diesem Fall nicht geändert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [getConnection-Methode &#40;SQLServerDataSource&#41;](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md)   
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
