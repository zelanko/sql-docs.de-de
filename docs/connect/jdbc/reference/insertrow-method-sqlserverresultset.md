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
manager: craigg
ms.openlocfilehash: 611ba86c25f78cda15fcac53d8f31311d88e4840
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47696869"
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
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
