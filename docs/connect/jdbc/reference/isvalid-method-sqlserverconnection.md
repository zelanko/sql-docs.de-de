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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 379d71b2100115bc1192a6f8f744b5afe92e5aed
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80921084"
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
  
  
