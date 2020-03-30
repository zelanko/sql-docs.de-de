---
title: isValid-Methode (SQLServerConnection) | Microsoft-Dokumentation
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
ms.openlocfilehash: 3915690475e5ce9321af7fc15498c2bde018c640
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67977129"
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
 **TRUE**, wenn die Verbindung gültig ist; **FALSE**, wenn die Verbindung ungültig ist oder die Gültigkeit der Verbindung nicht bestimmt werden kann, bevor ein Timeout zurückgegeben wird.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese isValid-Methode wird von der isValid-Methode in der java.sql.Connection-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
