---
title: setFetchDirection-Methode (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.setFetchDirection
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4ee82290-508d-4bff-a5c5-8a56338deef8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6f0055facd8248816da07fea74e8dc8035f78d84
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922357"
---
# <a name="setfetchdirection-method-sqlserverresultset"></a>setFetchDirection-Methode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt Aufschluss über die Richtung, in der die Zeilen in diesem [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt verarbeitet werden.  
  
> [!NOTE]  
>  Diese Methode wird von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] derzeit nicht unterstützt. Bei Verwendung dieser Methode wird die Einstellung vom JDBC-Treiber zwar gespeichert, sie wird jedoch derzeit nicht genutzt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setFetchDirection(int direction)  
```  
  
#### <a name="parameters"></a>Parameter  
 *direction*  
  
 Ein Wert vom Typ **int** zum Angeben der vorgeschlagenen Abrufrichtung. Es kann sich um einen der folgenden Werte handeln:  
  
 ResultSet.FETCH_FORWARD  
  
 ResultSet.FETCH_REVERSE  
  
 ResultSet.FETCH_UNKNOWN  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese setFetchDirection-Methode wird von der setFetchDirection-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Der Anfangswert dieser Methode wird vom [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt bestimmt, von dem dieses SQLServerResultSet-Objekt erstellt wurde. Die Abrufrichtung kann jedoch jederzeit geändert werden.  
  
> [!NOTE]  
>  Handelt es sich beim Cursortyp um einen Vorwärtscursor, hat die Verwendung dieser Methode keine Auswirkungen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
