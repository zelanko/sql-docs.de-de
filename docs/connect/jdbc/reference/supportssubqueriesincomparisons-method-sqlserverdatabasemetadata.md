---
title: SupportsSubqueriesInComparisons-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsSubqueriesInComparisons
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 467d32e6-b47e-4095-9f8b-73e07fb814e8
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: cbe03e6e976908d359e7f5f34879f67105c3d9a7
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66797270"
---
# <a name="supportssubqueriesincomparisons-method-sqlserverdatabasemetadata"></a>supportsSubqueriesInComparisons-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ab, ob von dieser Datenbank Unterabfragen in Vergleichsausdrücken unterstützt werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean supportsSubqueriesInComparisons()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** unterstützt. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese SupportsSubqueriesInComparisons-Methode wird von der SupportsSubqueriesInComparisons-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
