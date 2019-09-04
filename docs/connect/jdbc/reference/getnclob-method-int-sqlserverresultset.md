---
title: getNClob-Methode (int) (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 103082e3-de98-4dff-8dc7-eaa5c64b1597
author: MightyPen
ms.author: genemi
ms.openlocfilehash: dfe7b70d4a176832873bb9f5dcd7db3c8d8c553b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67981534"
---
# <a name="getnclob-method-int-sqlserverresultset"></a>getNClob-Methode (int) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft den Wert der angegebenen Spalte in der aktuellen Zeile des [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als NClob-Objekt in der Programmiersprache Java ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.NClob getNClob(int columnIndex)  
```  
  
#### <a name="parameters"></a>Parameter  
 *columnIndex*  
  
 Ein **ganzzahliger** Wert, der den Spaltenindex angibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein NCLOB-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getNClob-Methode wird von der getNClob-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Diese Methode wird nur für Spalten vom Typ " **nvarchar (max)** ", " **ntext**" und " **XML** " unterstützt. Bei Verwendung dieser Methode für andere Datentypen wird eine Ausnahme ausgelöst.  
  
## <a name="see-also"></a>Weitere Informationen  
 [getNClob-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getnclob-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
