---
title: usesLocalFiles-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.usesLocalFiles
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 69afb3a9-ed56-4191-88b8-bc46c03b817b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a88b6645445b9b9a4c644444ad3996377436112f
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "68001594"
---
# <a name="useslocalfiles-method-sqlserverdatabasemetadata"></a>usesLocalFiles-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ab, ob Tabellen von dieser Datenbank in einer lokalen Datei gespeichert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean usesLocalFiles()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Der Wert lautet **TRUE**, wenn die Datenbank lokale Dateien verwendet. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese usesLocalFiles-Methode wird von der usesLocalFiles-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
