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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c5dea8e183cb572bd0d70e9ccce01a203204b26c
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80925876"
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
 Diese getConnection-Methode wird von der getConnection-Methode in der javax.sql.DataSource-Schnittstelle angegeben.  
  
 Wenn die getConnection-Methode mit einem Benutzernamen oder Kennwort aufgerufen wird, dessen Wert nicht NULL ist, werden die Eigenschaften für den Benutzernamen und das Kennwort ersetzt, die bei der Initialisierung des SQLServerConnection-Objekts für die SQLServerDataSource-Klasse festgelegt werden. Beispiel: Hat der Aufrufer [setUser](../../../connect/jdbc/reference/setuser-method-sqlserverdatasource.md) und [setPassword](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md) für die Datenquelle aufgerufen und ruft anschließend getConnection auf und gibt einen Benutzernamen und ein Kennwort ungleich NULL an, werden der Benutzername und das Kennwort, der bzw. das durch setUser und setPassword festgelegt sind, durch das an getConnection weitergegebene Kennwort ersetzt.  
  
> [!NOTE]  
>  Benutzernamen und Kennwörter, die in der URL durch einen Aufruf der [setURL](../../../connect/jdbc/reference/seturl-method-sqlserverdatasource.md)-Methode festgelegt sind, werden in diesem Fall nicht geändert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [getConnection-Methode &#40;SQLServerDataSource&#41;](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md)   
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
