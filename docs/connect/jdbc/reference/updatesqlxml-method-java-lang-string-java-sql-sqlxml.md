---
title: updateSQLXML-Methode (java.lang.String, java.sql.SQLXML) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 60021881-ef83-499b-9977-e20ff23c1312
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0e2772b43c084e1780b8e65cd6425b67d01092f1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67998285"
---
# <a name="updatesqlxml-method-javalangstring-javasqlsqlxml"></a>updateSQLXML-Methode (java.lang.String, java.sql.SQLXML)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aktualisiert die angegebene Spalte mit einem java.sql.SQLXML-Wert.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void updateSQLXML(java.lang.String columnLabel,  
                         java.sql.SQLXML xmlObject)  
```  
  
#### <a name="parameters"></a>Parameter  
 *columnLabel*  
  
 Eine **Zeichenfolge**, die die Bezeichnung der Spalte angibt.  
  
 *xmlObject*  
  
 Ein SQLXML-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese updatesqlxml-Methode wird von der updatesqlxml-Methode in der Java. SQL. Resultset-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [updateSQLXML-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatesqlxml-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
