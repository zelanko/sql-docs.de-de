---
title: GetFetchDirection-Methode (SQLServerStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getFetchDirection
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ceb4ae68-decc-46d3-83f1-0bbd23aaf58c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3944990d8b6f551ba70545e5cacf42179e7b68ec
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47617088"
---
# <a name="getfetchdirection-method-sqlserverstatement"></a>getFetchDirection-Methode (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft die Richtung zum Abrufen von Zeilen aus Datenbanktabellen ab, die standardmäßig für Resultsets verwendet wird, die auf der Grundlage dieses [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekts generiert werden.  
  
> [!NOTE]  
>  Diese Methode wird von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] derzeit nicht implementiert. Aus diesem Grund wird immer "FETCH_UNKNOWN" zurückgegeben.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final int getFetchDirection()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert vom Typ **int** zum Angeben der Abrufrichtung, die von der [setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverstatement.md)-Methode angegeben wird.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese GetFetchDirection-Methode wird von der GetFetchDirection-Methode in der java.sql.Statement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerStatement-Elemente](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement-Klasse](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
