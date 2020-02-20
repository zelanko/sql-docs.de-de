---
title: Methode „createStatement(int, int)“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.createStatement (int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 90dbf639-c3d8-4519-9300-5447c79aec17
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 84afda93fa79d226eec21cb92c16ff5ebbc55fa5
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67955314"
---
# <a name="createstatement-method-int-int"></a>createStatement-Methode (int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Erstellt ein [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt, von dem [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekte mit dem angegebenen Typ und der angegebenen Parallelität generiert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.Statement createStatement(int resultSetType,  
                                          int resultSetConcurrency)  
```  
  
#### <a name="parameters"></a>Parameter  
 *resultSetType*  
  
 Der Wert vom Typ **int**, der den Resultsettyp darstellt.  
  
 *resultSetConcurrency*  
  
 Der Wert vom Typ **int**, der den Parallelitätstyp darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Das Statement-Objekt  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese createStatement-Methode wird von der createStatement-Methode in der java.sql.Connection-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [createStatement-Methode &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md)   
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
