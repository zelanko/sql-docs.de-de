---
title: SetDisableStatementPooling-Methode (SQLServerConnection) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setDisableStatementPooling
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d3d126126827674eb3164a800891c8f6afc502b3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47796918"
---
# <a name="setdisablestatementpooling-method-sqlserverconnection"></a>setDisableStatementPooling-Methode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Legt fest, anweisungspools "true" oder "false". False gibt an, können die Anweisung pooling in Kopplung mit statementpoolingcachesize-Wert-Wert > 0 verwendet werden soll.

## <a name="syntax"></a>Syntax  
  
```  
  
public void setDisableStatementPooling(boolean disableStatementPooling)  
```  

#### <a name="parameters"></a>Parameter  
 *disableStatementPooling*  
  
 Der neue Wert des der **DisableStatementPooling** Connection-Eigenschaft.  
 
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Diese Methode wird von JDBC Driver, Version 6.4 verfügbar und auf dem Weg.
 
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
