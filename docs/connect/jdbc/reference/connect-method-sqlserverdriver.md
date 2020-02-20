---
title: connect-Methode (SQLServerDriver) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDriver.connect
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 43813a4c-1cc7-4659-ba27-f1786f1371eb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 518be09d4a4929a06866eec253a49a39d7865263
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67955418"
---
# <a name="connect-method-sqlserverdriver"></a>connect-Methode (SQLServerDriver)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Stellt eine Verbindung mit der Datenbank her.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.Connection connect(java.lang.String Url,  
                                   java.util.Properties suppliedProperties)  
```  
  
#### <a name="parameters"></a>Parameter  
 *Url*  
  
 Ein **Zeichenfolgenwert** mit der URL, die zum Herstellen einer Verbindung mit der Datenbank verwendet wird.  
  
 *suppliedProperties*  
  
 Ein Satz von Stringwertpaaren, die als Verbindungsargumente verwendet werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Connection-Objekt  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese connect-Methode wird von der connect-Methode in der java.sql.Driver-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDriver-Methoden](../../../connect/jdbc/reference/sqlserverdriver-methods.md)   
 [SQLServerDriver-Elemente](../../../connect/jdbc/reference/sqlserverdriver-members.md)   
 [SQLServerDriver-Klasse](../../../connect/jdbc/reference/sqlserverdriver-class.md)  
  
  
