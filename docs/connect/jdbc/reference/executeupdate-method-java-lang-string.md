---
title: executeUpdate-Methode (java.lang.String, int[]) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.executeUpdate (java.lang.String, int[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7b3d5b60-4285-4047-b13e-106754ca0d98
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 059f463c6a448c6ae2ab302542a50cde1f533db8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67954703"
---
# <a name="executeupdate-method-javalangstring-int"></a>executeUpdate-Methode (java.lang.String, int[])
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Führt die angegebene SQL-Anweisung aus und signalisiert [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)], dass die automatisch generierten Schlüssel, die in dem angegebenen Array angegeben sind, zum Abrufen verfügbar gemacht werden sollen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final int executeUpdate(java.lang.String sql,  
                               int[] columnIndexes)  
```  
  
#### <a name="parameters"></a>Parameter  
 *sql*  
  
 Eine **Zeichenfolge** mit einer SQL-Anweisung.  
  
 *columnIndexes*  
  
 Ein Array von int-Werten zum Angeben der Spaltenindizes der automatisch generierten Schlüssel, die verfügbar gemacht werden sollen.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **int**-Wert, der die Anzahl der betroffenen Zeilen angibt, oder „0“ bei Verwendung einer DDL-Anweisung.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese executeUpdate-Methode wird von der executeUpdate-Methode in der java.sql.Statement-Schnittstelle angegeben.  
  
 Wenn das Ausführen einer gespeicherten Prozedur zu einer Updatezählung größer als 1 führt oder mehrere Resultsets generiert werden, führen Sie die gespeicherte Prozedur mit der [execute](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md)-Methode aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [executeUpdate-Methode &#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md)   
 [SQLServerStatement-Elemente](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement-Klasse](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
