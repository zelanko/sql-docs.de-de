---
title: GetString-Methode (Int) (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getString (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bfa493c4-fe07-449b-b4d0-384e1a1fce48
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 8690984c3795bb07497a3d255d85766930c1ab07
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66773884"
---
# <a name="getstring-method-int-sqlserverresultset"></a>getString-Methode (int) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft den Wert des angegebenen Spaltenindexes in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als **String-Objekt** in der Programmiersprache Java ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.lang.String getString(int columnIndex)  
```  
  
#### <a name="parameters"></a>Parameter  
 *columnIndex*  
  
 Ein **ganzzahliger** Wert, der den Spaltenindex angibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **String-Wert**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese getString-Methode wird von der getString-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Alle Spalten in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] können als String-Objekt zurückgegeben werden. D.h., es kann eine **String-Darstellung** aller zahlen- und zeichenfolgenbasierter Typen und eine hexadezimale String-Darstellung binärer Spalten wie binary, varbinary, varbinary(max), image, timestamp oder uniqueidentifier zurückgegeben werden.  
  
 Den Speicherort berücksichtigende Typen wie „money“, „smallmoney“, „datetime“, „smalldatetime“, „float“, „real“, „decimal“ oder „numeric“ geben für den zugrunde liegenden Wert des Typs das kanonische toString()-Format zurück.  
  
 Benutzerdefinierte Typen werden als hexadezimale **String-Werte** zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [getString-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getstring-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
