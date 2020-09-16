---
description: executeUpdate-Methode ()
title: Methode „executeUpdate()“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.executeUpdate ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ca534c6b-ef4d-4ae8-8cc3-514728623cff
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d0a973d76e44869c2eb7584bbc7127f4613a5139
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88437602"
---
# <a name="executeupdate-method-"></a>executeUpdate-Methode ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Führt die SQL-Anweisung in diesem [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)-Objekt aus. Hierbei muss es sich um eine SQL-Anweisung vom Typ „INSERT“, „UPDATE“, „MERGE“, „DELETE“ oder um eine SQL-Anweisung handeln, von der nichts zurückgegeben wird (z. B. eine DDL-Anweisung).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public int executeUpdate()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **int**-Wert, der die Anzahl der betroffenen Zeilen angibt, oder „0“ bei Verwendung einer DDL-Anweisung.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese executeUpdate-Methode wird von der executeUpdate-Methode in der java.sql.PreparedStatement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [executeUpdate-Methode &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/executeupdate-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement-Elemente](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement-Klasse](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
