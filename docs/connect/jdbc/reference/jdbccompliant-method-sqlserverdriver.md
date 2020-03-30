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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c36d7980355eed1e1a1e8f42fb53c75fdb70d0ed
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67976951"
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
  
  
