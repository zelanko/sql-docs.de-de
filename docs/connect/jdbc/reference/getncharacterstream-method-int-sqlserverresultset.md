---
title: getNCharacterStream-Methode (int) (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f1cfa4e4-3e1f-4504-b0de-cc626d653661
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c78a2289ce7332a06d3c9ef004a138afb8921cd9
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80905937"
---
# <a name="getncharacterstream-method-int-sqlserverresultset"></a>getNCharacterStream-Methode (int) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft den Wert einer angegebenen Spalte in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als Readerobjekt ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.io.Reader getNCharacterStream(int columnIndex)  
```  
  
#### <a name="parameters"></a>Parameter  
 *columnIndex*  
  
 Ein **ganzzahliger** Wert, der den Spaltenindex angibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Reader-Objekt  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getNCharacterStream-Methode wird von der getNCharacterStream-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Mit dieser Methode kann der Wert einer Spalte vom Typ **nvarchar**, **nchar**, **nvarchar(max)** , **ntext** oder **xml** in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts abgerufen werden. Beim Versuch, mit dieser Methode Werte anderer Datentypen abzurufen, wird eine Ausnahme ausgelöst.  
  
## <a name="see-also"></a>Weitere Informationen  
 [getNCharacterStream-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getncharacterstream-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)  
  
  
