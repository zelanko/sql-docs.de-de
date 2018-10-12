---
title: FindColumn-Methode (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.findColumn
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7c29994a-0b53-420b-8a9b-82a9eef08587
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a5ff2173990dabafab5297dd195e617825768aef
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47837728"
---
# <a name="findcolumn-method-sqlserverresultset"></a>findColumn-Methode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft für den angegebenen Spaltennamen den Index der ersten übereinstimmenden Spalte in diesem [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public int findColumn(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>Parameter  
 *columnName*  
  
 Eine **Zeichenfolge**, die den Namen der Spalte enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **ganzzahliger** Wert, der den Spaltenindex angibt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese FindColumn-Methode wird von der FindColumn-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Sind mehrere Spalten mit dem gleichen Namen vorhanden, wird von der findColumn-Methode die erste die Groß-/Kleinschreibung berücksichtigende Übereinstimmung zurückgegeben. Ist keine Groß-/Kleinschreibung berücksichtigende Übereinstimmung vorhanden, wird von der Methode die erste die Groß-/Kleinschreibung nicht berücksichtigende Übereinstimmung zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
