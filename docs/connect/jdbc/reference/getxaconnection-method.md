---
title: getxaconnetction-Methode () | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerXADataSource.getXAConnection ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b2710613-78b1-438f-b996-c7ae6f34381a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3c53cbcc5abcb9fb08999b1d171645b45097eb34
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67977971"
---
# <a name="getxaconnection-method-"></a>getXAConnection-Methode ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Stellt eine physische Datenbankverbindung her, die in einer verteilten Transaktion verwendet werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public javax.sql.XAConnection getXAConnection()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein xaconnetction-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 java.sql.SQLException  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getxaconnection-Methode wird von der getxaconnection-Methode in der javax. SQL. XADataSource-Schnittstelle angegeben.  
  
> [!NOTE]  
>  Diese Methode wird normalerweise von XA-Verbindungspoolimplementierungen und nicht vom regulären JDBC-Anwendungscode aufgerufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [getXAConnection-Methode &#40;SQLServerXADataSource&#41;](../../../connect/jdbc/reference/getxaconnection-method-sqlserverxadatasource.md)   
 [SQLServerXADataSource-Methoden](../../../connect/jdbc/reference/sqlserverxadatasource-methods.md)   
 [SQLServerXADataSource-Elemente](../../../connect/jdbc/reference/sqlserverxadatasource-members.md)   
 [SQLServerXADataSource-Klasse](../../../connect/jdbc/reference/sqlserverxadatasource-class.md)  
  
  
