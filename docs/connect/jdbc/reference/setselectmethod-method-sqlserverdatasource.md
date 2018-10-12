---
title: SetSelectMethod-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setSelectMethod
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7934276d-5ac9-4cbc-a2a0-2c65c93733ac
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 629c92aaf5ffb23976ad2e4ff2377cc53f87120d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47842558"
---
# <a name="setselectmethod-method-sqlserverdatasource"></a>setSelectMethod-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den Standardcursortyp fest, der für alle Resultsets verwendet wird, die mithilfe dieses [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)-Objekts erstellt werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setSelectMethod(java.lang.String selectMethod)  
```  
  
#### <a name="parameters"></a>Parameter  
 *selectMethod*  
  
 Ein Wert vom Typ **Zeichenfolge** mit dem Standardcursortyp.  
  
## <a name="remarks"></a>Remarks  
 "selectMethod" ist der Standardcursortyp, der für ein Resultset verwendet wird. Diese Eigenschaft ist nützlich für die Verarbeitung großer Resultsets ohne dass das gesamte Resultset im clientseitigen Speicher abgelegt wird. Wenn Sie die Eigenschaft auf "cursor" festlegen, können Sie einen serverseitigen Cursor erstellen, der jeweils kleinere Datenauschnitte abrufen kann. Wenn die selectMethod-Eigenschaft nicht festgelegt ist, gibt [getSelectMethod](../../../connect/jdbc/reference/getselectmethod-method-sqlserverdatasource.md) den Standardwert „direct“ zurück.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
