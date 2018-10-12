---
title: SQLServerStatement-Klasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ec24963c-8b51-4838-91e9-1fbfa2347451
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7488efcb3392623e6f54cff440a16494c10e0a69
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47705348"
---
# <a name="sqlserverstatement-class"></a>SQLServerStatement-Klasse
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Stellt die grundlegende Implementierung der JDBC-Anweisungsfunktion dar.  
  
 **Paket:** com.microsoft.sqlserver.jdbc  
  
 **Implementiert:** [ISQLServerStatement](../../../connect/jdbc/reference/isqlserverstatement-interface.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public class SQLServerStatement  
```  
  
## <a name="remarks"></a>Remarks  
 Von der SQLServerStatement-Klasse wird außerdem eine Reihe von Basisklassenimplementierungsmethoden für die JDBC-vorbereitete Anweisung und aufrufbare Anweisungen bereitgestellt. Standardmäßig werden von der SQLServerStatement-Klasse SQL-Anweisungen ausgeführt und anschließend Updatezählungen und Resultsets an die Benutzeranwendung zurückgegeben.  
  
 Diese Klasse unterstützt das Entpacken in die SQLServerStatement-Klasse, die ISQLServerStatement-Schnittstelle und der java.sql.Statement-Schnittstelle. Weitere Informationen finden Sie unter [Wrapper und Schnittstellen](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerStatement-Elemente](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [API-Referenz für den JDBC-Treiber](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
