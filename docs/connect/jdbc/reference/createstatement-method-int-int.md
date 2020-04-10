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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7e260135aa251012edfa98a08d4db3c358c17c51
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80927669"
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
  
  
