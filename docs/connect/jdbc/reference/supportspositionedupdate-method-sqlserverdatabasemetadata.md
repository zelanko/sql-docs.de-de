---
title: SupportsPositionedUpdate-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsPositionedUpdate
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f963fb70-377d-43f5-8d56-326591f6d3e9
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: da21e58e0decbf7e5cde83cf34d59182212232ba
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66797426"
---
# <a name="supportspositionedupdate-method-sqlserverdatabasemetadata"></a>supportsPositionedUpdate-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ab, ob positionierte UPDATE-Anweisungen von dieser Datenbank unterstützt werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean supportsPositionedUpdate()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** unterstützt. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese SupportsPositionedUpdate-Methode wird von der SupportsPositionedUpdate-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
