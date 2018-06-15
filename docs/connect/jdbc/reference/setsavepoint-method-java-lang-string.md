---
title: SetSavepoint-Methode (java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerConnection.setSavepoint (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1cf15ec4-d9d9-4ab3-bfee-2ea43ff609a6
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a38bd657439dab6c705c176b6bbe90ab5f643546
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "32845545"
---
# <a name="setsavepoint-method-javalangstring"></a>setSavepoint-Methode (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Erstellt einen Sicherungspunkt mit dem angegebenen Namen in der aktuellen Transaktion und gibt die neue [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md) Objekt, das sie darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.Savepoint setSavepoint(java.lang.String sName)  
```  
  
#### <a name="parameters"></a>Parameter  
 *sName*  
  
 Ein **Zeichenfolge** Wert, der den Namen des Sicherungspunkts enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Sicherungspunkt-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Hinweise  
 Diese SetSavePoint-Methode wird von der SetSavePoint-Methode in der java.sql.Connection-Schnittstelle angegeben.  
  
 Die *sName* Argument wird automatisch mit Escapezeichen versehen von der [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)].  
  
## <a name="see-also"></a>Siehe auch  
 [SetSavepoint-Methode &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/setsavepoint-method-sqlserverconnection.md)   
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
