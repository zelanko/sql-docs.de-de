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
manager: jroth
ms.openlocfilehash: 1ca9d0fede758b99f442a9553e4266e79fa81134
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66794030"
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
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerXAResource-Methoden](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [SQLServerXAResource-Elemente](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [SQLServerXAResource-Klasse](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
