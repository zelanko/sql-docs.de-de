---
description: getObjectInstance-Methode (SQLServerDataSourceObjectFactory)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 79510f1e28f6f8933b417ad17ecac34713e885e1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88435062"
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
  
## <a name="remarks"></a>Bemerkungen  
 Die getObjectInstance-Methode wird von der getObjectInstance-Methode in der javax.naming.spi.ObjectFactory-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSourceObjectFactory-Methoden](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-methods.md)   
 [SQLServerDataSourceObjectFactory-Elemente](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-members.md)   
 [SQLServerDataSourceObjectFactory-Klasse](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-class.md)  
  
  
