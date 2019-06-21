---
title: SetString-Methode (SQLServerCallableStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.setString
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f38b97b5-d4f0-4f74-a33d-740241a85842
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: abbb07c23685562d28297f096728589fdc3a343e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66773499"
---
# <a name="setstring-method-sqlservercallablestatement"></a>setString-Methode (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den angegebenen Parameter auf den angegebenen Java-**Zeichenfolgenwert** fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setString(java.lang.String sCol,  
                      java.lang.String s)  
```  
  
#### <a name="parameters"></a>Parameter  
 *sCol*  
  
 Eine **Zeichenfolge**, die den Namen des Parameters enthält.  
  
 *s*  
  
 Ein **String-Wert**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese setString-Methode wird von der setString-Methode in der java.sql.CallableStatement-Schnittstelle angegeben.  
  
 Konvertierungen von Zeichenfolgen zu Binärwerten werden nur ausgeführt, wenn [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] bekannt ist, dass der Zieltyp binär ist. Ist der zugrunde liegende Typ nicht bekannt, wird vom JDBC-Treiber das **Zeichenfolge**-Literal übergeben. Kann die Konvertierung vom Server nicht ausgeführt werden, wird ein Serverfehler zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerCallableStatement-Elemente](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement-Klasse](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
