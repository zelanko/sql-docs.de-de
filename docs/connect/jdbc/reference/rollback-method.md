---
title: rollback()-Methode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.rollback ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7adb6772-4047-4d8e-931d-b3d20eec44b5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 08eaa304a861ab697c8b9cc83446610740d13d11
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80903743"
---
# <a name="rollback-method-"></a>rollback-Methode ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Macht alle im Rahmen der aktuellen Transaktion vorgenommenen Änderungen rückgängig und hebt sämtliche Datenbanksperren auf, die derzeit von diesem [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt aufrecht erhalten werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void rollback()  
```  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese rollBack-Methode wird von der rollBack-Methode in der java.sql.Connection-Schnittstelle angegeben.  
  
 Die Methode sollte nur bei deaktiviertem Modus für automatische Commits verwendet werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [rollback-Methode &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/rollback-method-sqlserverconnection.md)   
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
