---
title: getDateTimeOffset(java.lang.string) (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e585927c-0dee-43fd-b71e-c9f1701790bd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a929b5869e58f4f1207b14474302fdb247251850
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67983855"
---
# <a name="getdatetimeoffsetjavalangstring-sqlserverresultset"></a>getDateTimeOffset(java.lang.string) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Diese Methode wurde in [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0 hinzugefügt.  
  
 Ruft den Wert der angegebenen Spalte unter Berücksichtigung des Parameterindexes als [DateTimeOffset-Klassenobjekt](../../../connect/jdbc/reference/datetimeoffset-class.md) in Java ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public microsoft.sql.DateTimeOffset getDateTimeOffset(String columnName)  
```  
  
#### <a name="parameters"></a>Parameter  
 *columnName*  
  
 Name der Spalte.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein [DateTimeOffset-Klassen](../../../connect/jdbc/reference/datetimeoffset-class.md) Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Sie können einen [DateTimeOffset-Klassen](../../../connect/jdbc/reference/datetimeoffset-class.md) Wert mit [SQLServerResultSet. updatedatetimeoffset](../../../connect/jdbc/reference/updatedatetimeoffset-sqlserverresultset.md)aktualisieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
