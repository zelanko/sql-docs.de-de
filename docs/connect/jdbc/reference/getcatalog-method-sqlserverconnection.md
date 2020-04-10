---
title: getCatalog-Methode (SQLServerConnection) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.getCatalog
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e87ef65f-4b5a-4e1c-8db5-7f0932390bb0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 482bf8e2928e423f326369223bd2148306712b39
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80921556"
---
# <a name="getcatalog-method-sqlserverconnection"></a>getCatalog-Methode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft den aktuellen Katalognamen dieses [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.lang.String getCatalog()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **String-Objekt**, das den Katalognamen enthält.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getCatalog-Methode wird von der getCatalog-Methode in der java.sql.Connection-Schnittstelle angegeben.  
  
 Gibt die aktuelle Katalogeigenschaft des SQLServerConnection-Objekts oder NULL zurück, wenn sie nicht festgelegt ist. Die Katalogeigenschaft wird durch die [setCatalog](../../../connect/jdbc/reference/setcatalog-method-sqlserverconnection.md)-Methode eindeutig festgelegt oder durch Lesen der Umgebungsänderung für TDS für den aktuellen Katalog implizit aktualisiert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
