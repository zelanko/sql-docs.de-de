---
title: IsValid-Methode (SQLServerConnection) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3b0a8bbf-9369-4456-9ab8-1434ccacdd7e
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 2868fb92161b5e3458e5c5e0dc72ebdef074b3e7
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66796315"
---
# <a name="isvalid-method-sqlserverconnection"></a>isValid-Methode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt an, ob dieses [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt noch geöffnet und gültig ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean isValid(int timeout)  
```  
  
#### <a name="parameters"></a>Parameter  
 *timeout*  
  
 Ein Wert vom Typ **int** zum Angeben der Anzahl von Sekunden, die auf die Überprüfung der Verbindung gewartet wird.  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** Wenn die Verbindung gültig ist. **"false"** , wenn die Verbindung ungültig ist, oder die Gültigkeit der Verbindung kann nicht bestimmt werden, bevor das Timeout abläuft.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese Methode "IsValid" wird von der Methode "IsValid" in der java.sql.Connection-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
