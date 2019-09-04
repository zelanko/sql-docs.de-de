---
title: Sqlserverxaconnetction-Klasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5ecb4bf1-b8d1-47cf-9cb1-7a18acc11ce2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 32d538e31ca3f4a0d9b23411ebcb7b282df46b33
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67970311"
---
# <a name="sqlserverxaconnection-class"></a>SQLServerXAConnection-Klasse
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Stellt JDBC-Verbindungen dar, die an verteilten Transaktionen (XA-Transaktionen) beteiligt sein können.  
  
 **Paket:** com.microsoft.sqlserver.jdbc  
  
 **Erweitert:** [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)  
  
 **Implementiert:** javax.sql.XAConnection  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public class SQLServerXAConnection  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Ein SQLServerXAConnection-Objekt kann in einer verteilten Transaktion mittels eines [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)-Objekts aufgelistet werden. Ein Transaktions-Manager, der normalerweise Teil eines Servers auf mittlerer Ebene ist, verwaltet ein sqlserverxaconnetction-Objekt über das sqlserverxaresource-Objekt.  
  
> [!NOTE]  
>  Anwendungsprogrammierer verwenden diese Schnittstelle normalerweise nicht direkt. Sie wird in erster Linie von einem Transaktions-Manager verwendet, der auf dem Server auf mittlerer Ebene arbeitet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerXAConnection-Elemente](../../../connect/jdbc/reference/sqlserverxaconnection-members.md)   
 [API-Referenz für den JDBC-Treiber](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
