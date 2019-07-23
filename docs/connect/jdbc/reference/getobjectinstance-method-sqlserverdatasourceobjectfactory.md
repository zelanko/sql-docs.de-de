---
title: getObjectInstance-Methode (SQLServerDataSourceObjectFactory) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSourceObjectFactory.getObjectInstance
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 0a1503e2-e991-4d70-a223-087fc63baf73
author: MightyPen
ms.author: genemi
ms.openlocfilehash: de25e608c9fbdbdf6ff91d08e7a6502765bb590e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67981051"
---
# <a name="getobjectinstance-method-sqlserverdatasourceobjectfactory"></a>getObjectInstance-Methode (SQLServerDataSourceObjectFactory)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft eine Instanz des angegebenen Datenquellenobjekts ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.lang.Object getObjectInstance(java.lang.Object ref,  
                                          javax.naming.Name name,  
                                          javax.naming.Context c,  
                                          java.util.Hashtable h)  
```  
  
#### <a name="parameters"></a>Parameter  
 *ref*  
  
 Ein **Object**-Wert.  
  
 *name*  
  
 Der Name des Objekts.  
  
 *c*  
  
 Der Kontext relativ zum angegebenen Namen.  
  
 *h*  
  
 Die Umgebung, die beim Erstellen des Objekts verwendet wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **Object**-Wert.  
  
## <a name="exceptions"></a>Ausnahmen  
 java.sql.SQLException  
  
## <a name="remarks"></a>Remarks  
 Diese getObjectInstance-Methode wird durch die getObjectInstance-Methode in der javax. naming. SPI. objectfactory-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSourceObjectFactory-Methoden](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-methods.md)   
 [SQLServerDataSourceObjectFactory-Elemente](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-members.md)   
 [SQLServerDataSourceObjectFactory-Klasse](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-class.md)  
  
  
