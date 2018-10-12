---
title: getNClob-Methode (java.lang.String) (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 36571f7c-b335-4249-8f83-51dcb6923aec
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9ee88668cd930fa83f27f1fa4d3eace212e8419e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47787948"
---
# <a name="getnclob-method-javalangstring-sqlserverresultset"></a>getNClob-Methode (java.lang.String) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft den Wert der angegebenen Spalte in der aktuellen Zeile des [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als NClob-Objekt in der Programmiersprache Java ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.NClob getNClob(java.lang.String columnLabel)  
```  
  
#### <a name="parameters"></a>Parameter  
 *columnLable*  
  
 Eine **Zeichenfolge**, die die Spaltenbezeichnung enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein NClob-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese GetNClob-Methode wird von der GetNClob-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Diese Methode wird nur unter unterstützt **nvarchar(max)**, **Ntext**, und **Xml** Spalten. Bei Verwendung dieser Methode für andere Datentypen wird eine Ausnahme ausgelöst.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [getNClob-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getnclob-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
