---
title: SetDisableStatementPooling-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4be547e1d5c37a00cd023bc542f3bb6e9f73e048
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47611048"
---
# <a name="setdisablestatementpooling-method-sqlserverdatasource"></a>setDisableStatementPooling-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den Wert für die **DisableStatementPooling** Connection-Eigenschaft. False gibt an, können die Anweisung pooling in Kopplung mit statementpoolingcachesize-Wert-Wert > 0 verwendet werden soll.  

## <a name="syntax"></a>Syntax  
  
```
public void setDisableStatementPooling(boolean disableStatementPooling);  
```  
  
#### <a name="parameters"></a>Parameter  
 *disableStatementPooling*  
  
 Der neue Wert des der **DisableStatementPooling** Connection-Eigenschaft.  

## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Diese Methode wird von JDBC Driver, Version 6.4 verfügbar und auf dem Weg.
 
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
