---
title: InsertRow-Methode (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.insertRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 363d1008-1396-4fc0-8e27-c9ba2499e7f1
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: cf6b427cfaaf736fb7ea3862554bde172f2a0247
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66801227"
---
# <a name="insertrow-method-sqlserverresultset"></a>insertRow-Methode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Fügt den Inhalt der Einfügezeile diesem [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt und der Datenbank hinzu.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void insertRow()  
```  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese InsertRow-Methode wird von der InsertRow-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Beim Aufruf dieser Methode muss sich der Cursor in der Einfügezeile befinden. Nach dem Aufruf dieser Methode verbleibt der Cursor in der Einfügezeile, und das Resultset im Einfügemodus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
