---
title: addBatch-Methode (SQLServerStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.addBatch
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 95924a8b-a43c-4133-aff6-1d712e60e234
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c19e8cd92f7ee7aafcf6dd23e9c179f2557e628f
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67955988"
---
# <a name="addbatch-method-sqlserverstatement"></a>addBatch-Methode (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Fügt den angegebenen SQL-Befehl der aktuellen Liste mit Befehlen für dieses [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt hinzu.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void addBatch(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>Parameter  
 *sql*  
  
 Eine **Zeichenfolge** mit einer SQL-Anweisung.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese addBatch-Methode wird von der addBatch-Methode in der java.sql.Statement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerStatement-Elemente](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement-Klasse](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
