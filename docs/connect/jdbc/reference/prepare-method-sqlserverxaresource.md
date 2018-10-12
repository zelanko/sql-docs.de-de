---
title: Prepare-Methode (SQLServerXAResource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerXAResource.prepare
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f800c966-3fae-41b3-963a-464988f80da3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5a16d143266823b9455c306cefa37c9a7618524d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47743648"
---
# <a name="prepare-method-sqlserverxaresource"></a>prepare-Methode (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Fordert an, dass der Ressourcen-Manager für eine Transaktions-Commit-Aktion der vom vorhandenen Xid-Objekt angegebenen Transaktion vorbereitet wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public int prepare(javax.transaction.xa.Xid xid)  
```  
  
#### <a name="parameters"></a>Parameter  
 *XID*  
  
 Ein Xid-Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **Int** Wert.  
  
## <a name="exceptions"></a>Ausnahmen  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>Remarks  
 Diese prepare-Methode wird von der prepare-Methode in der javax.transaction.xa.XAResource-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerXAResource-Methoden](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [SQLServerXAResource-Elemente](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [SQLServerXAResource-Klasse](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
