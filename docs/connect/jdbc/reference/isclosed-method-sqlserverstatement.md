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
manager: jroth
ms.openlocfilehash: 5e801fe11bcf26fd474290f7cac8c660b40e5b0b
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66796554"
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
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerStatement-Elemente](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement-Klasse](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
