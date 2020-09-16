---
description: executeQuery-Methode (java.lang.String)
title: executeQuery-Methode (java.lang.String) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.executeQuery (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 610205c2-6bcd-426c-ad6f-9682551efdec
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cff547cf27a6ef796e31383e524872717943b860
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88437702"
---
# <a name="executequery-method-javalangstring"></a>executeQuery-Methode (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Führt die angegebene SQL-Anweisung aus und gibt ein einzelnes [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final java.sql.ResultSet executeQuery(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>Parameter  
 *sql*  
  
 Eine **Zeichenfolge** mit einer SQL-Anweisung.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein SQLServerResultSet-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese executeQuery-Methode wird von der executeQuery-Methode in der java.sql.Statement-Schnittstelle angegeben.  
  
 Die Methode überschreibt die [executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverstatement.md)-Methode, die sich in der [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Klasse befindet.  
  
 Durch den Aufruf dieser Methode wird eine Ausnahme ausgelöst, da die SQL-Anweisung für das SQLServerPreparedStatement-Objekt bei der Erstellung des Objekts angegeben wird.  
  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) wird ausgelöst, wenn die angegebene SQL-Anweisung etwas anderes als ein einzelnes [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt erzeugt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [executeQuery-Methode &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement-Elemente](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement-Klasse](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
