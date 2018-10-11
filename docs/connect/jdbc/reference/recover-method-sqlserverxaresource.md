---
title: recover-Methode (SQLServerXAResource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerXAResource.recover
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 840ecfcf-0dd3-4b7b-976f-dc9a96cd1464
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8ec96cd3f56b1710268ae951e39e98866fe1bd54
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47826818"
---
# <a name="recover-method-sqlserverxaresource"></a>recover-Methode (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft eine Liste vorbereiteter Transaktionszweige von einem Ressourcen-Manager ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public javax.transaction.xa.Xid[] recover(int flags)  
```  
  
#### <a name="parameters"></a>Parameter  
 *flags*  
  
 Ein **Int** -Wert, der einen der folgenden Werte annehmen kann: XAResource.TMSTARTRSCAN oder XAResource.TMENDRSCAN oder XAResource.TMNOFLAGS oder XAResource.TMSTARTTRSCAN | XAResource.TMENDRSCAN.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Xid-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>Remarks  
 Diese recover-Methode wird von der recover-Methode in der javax.transaction.xa.XAResource-Schnittstelle angegeben.  
  
 Wenn der Parameter **Flag** ist kein XAResource.TMSTARTRSCAN oder XAResource.TMSTARTRSCAN | XAResource.TMENDRSCAN, muss eine Überprüfung für die Wiederherstellung ausgeführt werden.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerXAResource-Methoden](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [SQLServerXAResource-Elemente](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [SQLServerXAResource-Klasse](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
