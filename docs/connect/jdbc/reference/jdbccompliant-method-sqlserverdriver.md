---
title: jdbcCompliant-Methode (SQLServerDriver) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDriver.jdbcCompliant
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b299b20d-d1cd-45b3-91dc-dcf579498570
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3ae5ac88d0427a605493bc19786bdd5f23dc93b6
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80915063"
---
# <a name="jdbccompliant-method-sqlserverdriver"></a>jdbcCompliant-Methode (SQLServerDriver)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Überprüft, ob [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] mit der JDBC-Spezifikation kompatibel ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean jdbcCompliant()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Der Wert ist **TRUE**, wenn der JDBC-Treiber die Mindestanforderungen erfüllt. Andernfalls lautet der Wert **false**.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese jdbcCompliant-Methode wird von der jdbcCompliant-Methode in der java.sql.Driver-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDriver-Methoden](../../../connect/jdbc/reference/sqlserverdriver-methods.md)   
 [SQLServerDriver-Elemente](../../../connect/jdbc/reference/sqlserverdriver-members.md)   
 [SQLServerDriver-Klasse](../../../connect/jdbc/reference/sqlserverdriver-class.md)  
  
  
