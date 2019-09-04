---
title: GetPropertyInfo-Methode (SQLServerDriver) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDriver.getPropertyInfo
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b5eaad8a-31ef-44ac-af11-d5caa13ac3e2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d89a29af5aa3d2518f94101854371cea757e135c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67980669"
---
# <a name="getpropertyinfo-method-sqlserverdriver"></a>getPropertyInfo-Methode (SQLServerDriver)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Dient zum Ermitteln der erforderlichen Eigenschaften zum Herstellen einer Datenbankverbindung.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.DriverPropertyInfo[] getPropertyInfo(java.lang.String Url,  
                                                     java.util.Properties Info)  
```  
  
#### <a name="parameters"></a>Parameter  
 *Url*  
  
 Ein **Zeichenfolgenwert** mit der URL, die zum Herstellen einer Verbindung mit der Datenbank verwendet wird.  
  
 *Info*  
  
 Eine Liste mit Eigenschaftswertpaaren (bei der ersten Verwendung NULL).  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Array von driverpropertyinfo-Objekten.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese GetPropertyInfo-Methode wird von der GetPropertyInfo-Methode in der Java. SQL. Driver-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDriver-Methoden](../../../connect/jdbc/reference/sqlserverdriver-methods.md)   
 [SQLServerDriver-Elemente](../../../connect/jdbc/reference/sqlserverdriver-members.md)   
 [SQLServerDriver-Klasse](../../../connect/jdbc/reference/sqlserverdriver-class.md)  
  
  
