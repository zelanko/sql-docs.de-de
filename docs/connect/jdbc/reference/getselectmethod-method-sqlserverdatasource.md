---
title: getSelectMethod-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getSelectMethod
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b6255d2e-0028-474a-afa8-553ef092243e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 849768edee2b6eaebceecf190f9b35dce81372b6
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80929220"
---
# <a name="getselectmethod-method-sqlserverdatasource"></a>getSelectMethod-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt den Standardcursortyp zurück, der für alle Resultsets verwendet wird, die mithilfe dieses [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)-Objekts erstellt werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.lang.String getSelectMethod()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert vom Typ **Zeichenfolge** mit dem Standardcursortyp.  
  
## <a name="remarks"></a>Bemerkungen  
 Die selectMethod-Eigenschaft gibt den Standardcursortyp an, der für ein Resultset verwendet wird. Diese Eigenschaft ist nützlich für die Verarbeitung großer Resultsets ohne dass das gesamte Resultset im clientseitigen Speicher abgelegt wird. Wenn Sie die Eigenschaft auf "cursor" festlegen, können Sie einen serverseitigen Cursor erstellen, der jeweils kleinere Datenauschnitte abrufen kann. Wenn die selectMethod-Eigenschaft nicht festgelegt ist, gibt getSelectMethod den Standardwert "direct" zurück.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
