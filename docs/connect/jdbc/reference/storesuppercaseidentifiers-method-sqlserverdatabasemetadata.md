---
title: storesUpperCaseIdentifiers-Methode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.storesUpperCaseIdentifiers
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a622b748-d10b-4f02-afe3-fba4a5bca17b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 17b42f50fe28ba9d727ea6c897280dcd36034038
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67969886"
---
# <a name="storesuppercaseidentifiers-method-sqlserverdatabasemetadata"></a>storesUpperCaseIdentifiers-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ab, ob bei SQL-Bezeichnern mit gemischter Groß-/Kleinschreibung, die nicht in Anführungszeichen gesetzt sind, die Groß-/Kleinschreibung nicht berücksichtigt wird und die Bezeichner in Großbuchstaben gespeichert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean storesUpperCaseIdentifiers()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Der Wert **TRUE** wird zurückgegeben, wenn die Bezeichner mit Großschreibung gespeichert werden. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese storesUpperCaseIdentifiers-Methode wird von der storesUpperCaseIdentifiers-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
