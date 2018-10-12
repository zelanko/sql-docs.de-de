---
title: Start-Methode (SQLServerXAResource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerXAResource.start
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 33c90213-92f7-416b-b2fa-67a1afe64e97
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 269589e0ca54a5dd2c1325ee8c7b4e8672f61175
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47810168"
---
# <a name="start-method-sqlserverxaresource"></a>start-Methode (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Startet die Arbeit am Xid-Objekt, das in einem Transaktionszweig angegeben ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void start(javax.transaction.xa.Xid xid,  
                  int flags)  
```  
  
#### <a name="parameters"></a>Parameter  
 *XID*  
  
 Ein Xid-Objekt.  
  
 *flags*  
  
 Ein **Int** Wert.  
  
## <a name="exceptions"></a>Ausnahmen  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>Remarks  
 Diese start-Methode wird von der start-Methode in der javax.transaction.xa.XAResource-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerXAResource-Methoden](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [SQLServerXAResource-Elemente](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [SQLServerXAResource-Klasse](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
