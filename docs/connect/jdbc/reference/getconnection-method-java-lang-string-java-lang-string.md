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
manager: craigg
ms.openlocfilehash: f72babc3375c0720807322520a9761cb49e05919
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47677458"
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
  
## <a name="remarks"></a>Remarks  
 Diese GetConnection-Methode wird durch die GetConnection-Methode in der javax.sql.DataSource-Schnittstelle angegeben.  
  
 Aufrufen der GetConnection ersetzt-Methode mit einer nicht-Null-Benutzername oder Kennwort die Benutzereigenschaften für Namen und das Kennwort, die auf der SQLServerDataSource-Klasse festgelegt werden, wenn das SQLServerConnection-Objekt zu initialisieren. Beispiel: Hat der Aufrufer [setUser](../../../connect/jdbc/reference/setuser-method-sqlserverdatasource.md) und [setPassword](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md) für die Datenquelle aufgerufen und ruft anschließend getConnection auf und gibt einen Benutzernamen und ein Kennwort ungleich NULL an, werden der Benutzername und das Kennwort, der bzw. das durch setUser und setPassword festgelegt sind, durch das an getConnection weitergegebene Kennwort ersetzt.  
  
> [!NOTE]  
>  Benutzernamen und Kennwörter, die in der URL durch einen Aufruf der [setURL](../../../connect/jdbc/reference/seturl-method-sqlserverdatasource.md)-Methode festgelegt sind, werden in diesem Fall nicht geändert.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [getConnection-Methode &#40;SQLServerDataSource&#41;](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md)   
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
