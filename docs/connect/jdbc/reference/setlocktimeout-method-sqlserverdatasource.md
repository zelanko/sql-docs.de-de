---
title: SetLockTimeout-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setLockTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 10dca5aa-1851-4326-9ae9-7a8430d12d11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3f68cb1fa7df0b9de3ac18a5f8166f99f0d0e51d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47687728"
---
# <a name="setlocktimeout-method-sqlserverdatasource"></a>setLockTimeout-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt einen Wert vom Typ **int** fest, der angibt, wie lange von der Datenbank bis zum Melden eines Sperrtimeouts gewartet wird (in Millisekunden).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setLockTimeout(int lockTimeout)  
```  
  
#### <a name="parameters"></a>Parameter  
 *lockTimeout*  
  
 Ein Wert vom Typ **int**, der die Wartedauer in Millisekunden enthält.  
  
## <a name="remarks"></a>Remarks  
 Das Sperrtimeout ist die Anzahl von Millisekunden bis zur Meldung eines Sperrtimeouts durch die Datenbank. Der Standardwert "-1" bedeutet, dass unbegrenzt gewartet wird. Wird dieser Wert angegeben, stellt er den Standardwert für alle Anweisungen der Verbindung dar.  
  
> [!NOTE]  
>  Bei dem Wert "0" wird nicht gewartet. Ist die lockTimeout-Eigenschaft nicht festgelegt, wird von der [getLockTimeout](../../../connect/jdbc/reference/getlocktimeout-method-sqlserverdatasource.md)-Methode der Standardwert „-1“ zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
