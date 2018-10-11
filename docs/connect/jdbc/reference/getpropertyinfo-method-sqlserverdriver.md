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
manager: craigg
ms.openlocfilehash: 889f530496dd5fa975822702282cc78b99197318
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47624848"
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
 Ein Array von DriverPropertyInfo-Objekten.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese GetPropertyInfo-Methode wird von der GetPropertyInfo-Methode in der java.sql.Driver-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDriver-Methoden](../../../connect/jdbc/reference/sqlserverdriver-methods.md)   
 [SQLServerDriver-Elemente](../../../connect/jdbc/reference/sqlserverdriver-members.md)   
 [SQLServerDriver-Klasse](../../../connect/jdbc/reference/sqlserverdriver-class.md)  
  
  
