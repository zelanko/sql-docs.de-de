---
title: GetMaxFieldSize-Methode (SQLServerStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getMaxFieldSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ed7bbcb8-660b-4e9b-8241-e216c42826f9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: de123b3c6c8f0105a7280c87a4983fadc657ad93
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47795608"
---
# <a name="getmaxfieldsize-method-sqlserverstatement"></a>getMaxFieldSize-Methode (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft die maximale Anzahl von Bytes ab, die für Zeichen- und Binärspaltenwerte in einem [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt zurückgegeben werden können, das von diesem [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt erstellt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final int getMaxFieldSize()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Element vom Typ **int**, das die maximale Anzahl von Bytes anzeigt, die eine Spalte enthalten kann. Oder es wird „0“ angezeigt, wenn keine Grenze vorhanden ist.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese GetMaxFieldSize-Methode wird von der GetMaxFieldSize-Methode in der java.sql.Statement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerStatement-Methoden](../../../connect/jdbc/reference/sqlserverstatement-methods.md)   
 [SQLServerStatement-Klasse](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
