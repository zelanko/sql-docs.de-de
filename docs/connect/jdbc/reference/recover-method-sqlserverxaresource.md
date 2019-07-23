---
title: Recover-Methode (sqlserverxaresource) | Microsoft-Dokumentation
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
ms.openlocfilehash: 92d7b0db997a6b77b43efb6d8104f629bb5507e3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67976019"
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
  
 Ein **int** -Wert, der einen der folgenden Werte annehmen kann: "XAResource. tmstartrscan" oder "XAResource. tmendrscan" oder "XAResource. tmnoflags" oder "XAResource. tmstarttrscan" | XAResource. tmendrscan.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein xid-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>Remarks  
 Diese recover-Methode wird von der recover-Methode in der javax.transaction.xa.XAResource-Schnittstelle angegeben.  
  
 Wenn das parameter **flag** nicht "XAResource. tmstartrscan" oder "XAResource. tmstartrscan" ist | XAResource. tmendrscan: Es muss eine Wiederherstellungs Überprüfung ausgeführt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerXAResource-Methoden](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [SQLServerXAResource-Elemente](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [SQLServerXAResource-Klasse](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
