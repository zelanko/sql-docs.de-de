---
title: Methode „recover“ (SQLServerXAResource) | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b78165b8c199a04d716d18614e6fb56232eca429
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923120"
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
  
 Ein **int**-Wert, der einen der folgenden Werte aufweisen kann: XAResource.TMSTARTRSCAN oder XAResource.TMENDRSCAN oder XAResource.TMNOFLAGS oder XAResource.TMSTARTTRSCAN | XAResource.TMENDRSCAN.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Xid-Objekt  
  
## <a name="exceptions"></a>Ausnahmen  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>Bemerkungen  
 Diese recover-Methode wird von der recover-Methode in der javax.transaction.xa.XAResource-Schnittstelle angegeben.  
  
 Wenn der **flag**-Parameter keinen der Werte XAResource.TMENDRSCAN oder XAResource.TMSTARTRSCAN | XAResource.TMENDRSCAN aufweist, muss ein Wiederherstellungsscan ausgeführt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerXAResource-Methoden](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [SQLServerXAResource-Elemente](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [SQLServerXAResource-Klasse](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
