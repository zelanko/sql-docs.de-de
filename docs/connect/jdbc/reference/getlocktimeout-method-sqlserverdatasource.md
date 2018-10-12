---
title: GetLockTimeout-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getLockTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 676094e9-ec18-4524-9b21-1f9c5b16dd52
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 25b16ae2c31233ee837c86cc156ddcb2d4ffa901
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47660318"
---
# <a name="getlocktimeout-method-sqlserverdatasource"></a>getLockTimeout-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt einen Wert vom Typ **int** zurück, mit dem angegeben wird, wie lange von der Datenbank bis zum Melden eines Sperrtimeouts gewartet wird (in Millisekunden).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public int getLockTimeout()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert vom Typ **int** mit der Anzahl von Millisekunden, die die Datenbank warten wird.  
  
## <a name="remarks"></a>Remarks  
 Das Sperrtimeout ist die Anzahl von Millisekunden bis zur Meldung eines Sperrtimeouts durch die Datenbank. Der Standardwert "-1" bedeutet, dass unbegrenzt gewartet wird. Wird dieser Wert angegeben, stellt er den Standardwert für alle Anweisungen der Verbindung dar.  
  
> [!NOTE]  
>  Bei dem Wert "0" wird nicht gewartet. Ist die lockTimeout-Eigenschaft nicht festgelegt, wird von der getLockTimeout-Methode der Standardwert "-1" zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
