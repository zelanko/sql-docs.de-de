---
title: AcceptsURL-Methode (SQLServerDriver) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDriver.acceptsURL
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: fc744566-7191-4b15-9f76-b4b8087fb14a
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 3ca37a11eba988f0a4b65281ca6f6f4b0e83863f
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66783537"
---
# <a name="acceptsurl-method-sqlserverdriver"></a>acceptsURL-Methode (SQLServerDriver)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Überprüft, ob die angegebene URL gültig ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean acceptsURL(java.lang.String url)  
```  
  
#### <a name="parameters"></a>Parameter  
 *url*  
  
 Ein **Zeichenfolge** Wert, die mit der URL verwendet, um mit der Datenbank herstellen.  
  
## <a name="return-value"></a>Rückgabewert  
 Der Wert ist **true**, wenn die angegebene URL gültig ist. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese AcceptsURL-Methode wird von der AcceptsURL-Methode in der java.sql.Driver-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDriver-Methoden](../../../connect/jdbc/reference/sqlserverdriver-methods.md)   
 [SQLServerDriver-Elemente](../../../connect/jdbc/reference/sqlserverdriver-members.md)   
 [SQLServerDriver-Klasse](../../../connect/jdbc/reference/sqlserverdriver-class.md)  
  
  
