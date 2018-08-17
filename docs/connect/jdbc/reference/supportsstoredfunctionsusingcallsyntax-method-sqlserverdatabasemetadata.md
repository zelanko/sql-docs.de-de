---
title: SupportsStoredFunctionsUsingCallSyntax-Methode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0e5c0579-84b5-4717-b128-0bcd512f6022
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6c09d5fad34a20caefb670e3dbaed17b50e53215
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "37988382"
---
# <a name="supportsstoredfunctionsusingcallsyntax-method-sqlserverdatabasemetadata"></a>supportsStoredFunctionsUsingCallSyntax-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt an, ob von der aktuellen Datenbank das Aufrufen benutzer- oder herstellerdefinierter Funktionen mithilfe der Escapesyntax für gespeicherte Prozeduren unterstützt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean supportsStoredFunctionsUsingCallSyntax()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** unterstützt. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese SupportsStoredFunctionsUsingCallSyntax-Methode wird von der SupportsStoredFunctionsUsingCallSyntax-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
