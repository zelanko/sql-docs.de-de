---
title: IsClosed-Methode (SQLServerStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e79b5b53-16b0-42a3-be4e-542a77a21e12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bbd0e8ce34d14f0ef9fa77f3c2f64cc4e5804fb5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47718328"
---
# <a name="isclosed-method-sqlserverstatement"></a>isClosed-Methode (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt an, ob dieses [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt geschlossen wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean isClosed()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** Wenn diese [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) Objekt ist geschlossen, **"false"** , wenn es noch geöffnet ist.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese IsClosed-Methode wird von der IsClosed-Methode in der java.sql.Statement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerStatement-Elemente](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement-Klasse](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
