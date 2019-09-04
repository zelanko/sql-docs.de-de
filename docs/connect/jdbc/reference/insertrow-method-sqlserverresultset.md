---
title: insertRow-Methode (SQLServerResultSet) | Microsoft-Dokumentation
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
ms.openlocfilehash: 0f2e6148572d6ec6c7e9b52a704d79e8a9124ccf
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67977880"
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
  
## <a name="remarks"></a>Bemerkungen  
 Diese insertRow-Methode wird von der insertRow-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Beim Aufruf dieser Methode muss sich der Cursor in der Einfügezeile befinden. Nach dem Aufruf dieser Methode verbleibt der Cursor in der Einfügezeile, und das Resultset im Einfügemodus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
