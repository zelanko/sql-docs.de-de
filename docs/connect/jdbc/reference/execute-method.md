---
title: Methode „execute()“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.execute ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: fa96d0f8-101b-422f-a767-405be9a5f74f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9f7e87040fa74954435ed52f9923568e8bfed3fd
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67954926"
---
# <a name="execute-method-"></a>execute-Methode ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Führt die SQL-Anweisung in diesem [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)-Objekt aus. Hierbei kann es sich um eine beliebige Art von SQL-Anweisung handeln.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean execute()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Der Wert lautet **TRUE**, wenn die Anweisung ein Resultset zurückgibt. Der Wert lautet **FALSE**, wenn die Anweisung einen aktualisierten Zählerwert oder kein Ergebnis zurückgibt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese execute-Methode wird von der execute-Methode in der java.sql.PreparedStatement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [execute-Methode &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/execute-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement-Elemente](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement-Klasse](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
