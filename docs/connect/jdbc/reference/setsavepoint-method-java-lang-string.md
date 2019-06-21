---
title: SetSavepoint-Methode (java.lang.String) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setSavepoint (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1cf15ec4-d9d9-4ab3-bfee-2ea43ff609a6
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 41d9cf40028efb2fac732ec7f6da4a3be39095af
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66796806"
---
# <a name="setsavepoint-method-javalangstring"></a>setSavepoint-Methode (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Erstellt in der aktuellen Transaktion einen Sicherungspunkt mit dem angegebenen Namen und gibt das neue [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md)-Objekt zurück, das für den Sicherungspunkt steht.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.Savepoint setSavepoint(java.lang.String sName)  
```  
  
#### <a name="parameters"></a>Parameter  
 *sName*  
  
 Ein Wert vom Typ **Zeichenfolge** mit dem Namen des Sicherungspunkts.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Objekt des Sicherungspunkts.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese SetSavePoint-Methode wird von der SetSavePoint-Methode in der java.sql.Connection-Schnittstelle angegeben.  
  
 Das *sName*-Argument wird von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] automatisch mit Escapezeichen versehen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [setSavepoint-Methode &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/setsavepoint-method-sqlserverconnection.md)   
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
