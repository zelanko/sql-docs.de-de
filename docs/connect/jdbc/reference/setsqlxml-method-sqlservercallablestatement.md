---
title: SetSQLXML-Methode (SQLServerCallableStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: de095cb3-1111-4154-8996-3c2e529e3000
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3852a1251bb1f7567276529c1f15f5863ea69731
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47800928"
---
# <a name="setsqlxml-method-sqlservercallablestatement"></a>setSQLXML-Methode (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den angegebenen Parameter auf das angegebene SQLXML-Objekt fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final void setSQLXML(java.lang.String parameterName,  
                            java.sql.SQLXML xmlObject)  
```  
  
#### <a name="parameters"></a>Parameter  
 *parameterName*  
  
 Eine **Zeichenfolge** zum Angeben des Parameternamens.  
  
 *xmlObject*  
  
 Ein SQLXML-Objekt, das den Parameterwert enthält.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese setSQLXML-Methode wird von der setSQLXML-Methode in der java.sql.CallableStatement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerCallableStatement-Elemente](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
