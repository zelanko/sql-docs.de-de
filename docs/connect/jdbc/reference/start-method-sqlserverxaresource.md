---
title: start-Methode (SQLServerXAResource) | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c15f96b8375904a42d7f246212db264d1801899a
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80925638"
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
 *xid*  
  
 Ein Xid-Objekt  
  
 *flags*  
  
 Ein **int**-Wert  
  
## <a name="exceptions"></a>Ausnahmen  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>Bemerkungen  
 Diese start-Methode wird von der start-Methode in der javax.transaction.xa.XAResource-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerXAResource-Methoden](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [SQLServerXAResource-Elemente](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [SQLServerXAResource-Klasse](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
