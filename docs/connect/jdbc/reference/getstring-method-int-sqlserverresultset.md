---
title: getString-Methode (int) (SQLServerResultSet)
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerResultSet.getString (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bfa493c4-fe07-449b-b4d0-384e1a1fce48
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 24622aafce61bd5e4fe0faf07ee23d863a7c3628
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42786465"
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
 Diese GetString-Methode wird von der GetString-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Alle Spalten in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] können als String-Objekt zurückgegeben werden. D.h., es kann eine **String-Darstellung** aller zahlen- und zeichenfolgenbasierter Typen und eine hexadezimale String-Darstellung binärer Spalten wie binary, varbinary, varbinary(max), image, timestamp oder uniqueidentifier zurückgegeben werden.  
  
 Den Speicherort berücksichtigende Typen wie „money“, „smallmoney“, „datetime“, „smalldatetime“, „float“, „real“, „decimal“ oder „numeric“ geben für den zugrunde liegenden Wert des Typs das kanonische toString()-Format zurück.  
  
 Benutzerdefinierte Typen werden als hexadezimale **String-Werte** zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [getString-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getstring-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
