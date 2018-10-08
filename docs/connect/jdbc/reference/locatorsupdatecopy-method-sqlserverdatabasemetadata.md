---
title: LocatorsUpdateCopy-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.locatorsUpdateCopy
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f6ec8c1d-7ff8-4bc5-8bd3-0199a9294a6e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e98a27b0afb23d0631d6d0bc0b5569324dea5d73
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47758018"
---
# <a name="locatorsupdatecopy-method-sqlserverdatabasemetadata"></a>locatorsUpdateCopy-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt an, ob Aktualisierungen für ein LOB an einer Kopie oder direkt am LOB vorgenommen werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean locatorsUpdateCopy()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** Wenn Updates auf eine Kopie vorgenommen werden. **"false"** Wenn direkte Updates vorgenommen werden.  
  
## <a name="exceptions"></a>Ausnahmen  
 java.sql.SQLException  
  
## <a name="remarks"></a>Remarks  
 Diese LocatorsUpdateCopy-Methode wird von der LocatorsUpdateCopy-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
