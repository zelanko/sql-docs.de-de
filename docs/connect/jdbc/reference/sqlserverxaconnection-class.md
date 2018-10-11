---
title: SQLServerXAConnection-Klasse | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 1f2cc7956f36ee6fad113efd1cfe5afd5f58baff
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47782988"
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
  
## <a name="remarks"></a>Remarks  
 Ein SQLServerXAConnection-Objekt kann in einer verteilten Transaktion mittels eines [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)-Objekts aufgelistet werden. Ein Transaktions-Manager, in der Regel Teil des Servers auf mittlerer Ebene, verwaltet ein SQLServerXAConnection-Objekt, über das SQLServerXAResource-Objekt.  
  
> [!NOTE]  
>  Anwendungsprogrammierer verwenden diese Schnittstelle normalerweise nicht direkt. Sie wird in erster Linie von einem Transaktions-Manager verwendet, der auf dem Server auf mittlerer Ebene arbeitet.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerXAConnection-Elemente](../../../connect/jdbc/reference/sqlserverxaconnection-members.md)   
 [API-Referenz für den JDBC-Treiber](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
