---
title: GetTimestamp-Methode (Int, java.util.Calendar) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getTimestamp (int, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 161c559a-8651-44ba-a914-15eb6a612417
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fc078598377ec7a866b90d68677cfd9302b6263a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47673148"
---
# <a name="gettimestamp-method-int-javautilcalendar"></a>getTimestamp-Methode (int, java.util.Calendar)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft den Wert des angegebenen Parameters als java.sql.Timestamp-Objekt in der Programmiersprache Java ab (unter Berücksichtigung des vorhandenen Parameterindexes), indem ein Calendar-Objekt verwendet wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.Timestamp getTimestamp(int index,  
                                       java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Parameter  
 *Index*  
  
 Ein Wert vom Typ **int** zum Angeben des Parameterindexes.  
  
 *CAL*  
  
 Ein Kalenderobjekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Zeitstempel-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese getTimestamp-Methode wird von der getTimestamp-Methode in der java.sql.CallableStatement-Schnittstelle angegeben.  
  
 Von dieser Methode werden nur Werte aus **datetime**- und **smalldatetime**-Spalten von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [getTimestamp-Methode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/gettimestamp-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement-Elemente](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement-Klasse](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
