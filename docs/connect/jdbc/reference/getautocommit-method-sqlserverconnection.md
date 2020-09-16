---
description: getAutoCommit-Methode (SQLServerConnection)
title: getAutoCommit-Methode (SQLServerConnection) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.getAutoCommit
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: af1f67f4-f568-4e58-abcc-5c809a89b547
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 887e60b7bc390d323f890e6cb9552489ff15cfab
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88437352"
---
# <a name="getautocommit-method-sqlserverconnection"></a>getAutoCommit-Methode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft für dieses [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt den aktuellen Modus für automatische Commits ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean getAutoCommit()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **TRUE**, wenn der Modus für automatische Commits aktiviert ist; **FALSE**, wenn dies nicht der Fall ist.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getAutoCommit-Methode wird von der getAutoCommit-Methode in der java.sql.Connection-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
