---
title: setDate(java.lang.String, java.sql.Date)-Methode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.setDate (java.lang.String, java.sql.Date)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4762e2bd-5e94-4562-97d5-f023ecffc08c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6866a4c91a05911eccde71993db8526e8301c152
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80901939"
---
# <a name="setdate-method-javalangstring-javasqldate"></a>setDate-Methode (java.lang.String, java.sql.Date)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den angegebenen Parameter auf den angegebenen Datumswert fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setDate(java.lang.String sCol,  
                    java.sql.Date d)  
```  
  
#### <a name="parameters"></a>Parameter  
 *sCol*  
  
 Ein **String-Objekt**, das den Parameternamen enthält.  
  
 *d*  
  
 Ein Date-Objekt  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese setDate-Methode wird von der setDate-Methode in der java.sql.CallableStatement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerCallableStatement-Elemente](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement-Klasse](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
