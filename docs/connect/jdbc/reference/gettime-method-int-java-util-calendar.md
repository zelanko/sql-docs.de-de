---
title: getTime-Methode (int, java.util.Calendar) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getTime (int, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 87b7fbaf-7149-494f-b3b2-16b468a8ebf1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 33f5e25d45f1e08c30f3094a9200291de9510150
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67979106"
---
# <a name="gettime-method-int-javautilcalendar"></a>getTime-Methode (int, java.util.Calendar)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft unter Verwendung des angegebenen Calendar-Objekts den Wert des angegebenen Parameters als java.sql.Time-Objekt in der Programmiersprache Java ab (unter Berücksichtigung des vorhandenen Parameterindexes).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.Time getTime(int index,  
                             java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Parameter  
 *Index*  
  
 Ein Wert vom Typ **int** zum Angeben des Parameterindexes.  
  
 *cal*  
  
 Ein Kalender Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Zeit Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese getTime-Methode wird von der getTime-Methode in der java.sql.CallableStatement-Schnittstelle angegeben.  
  
 Finden Sie im Diagramm, das mit dem Titel "Konvertierungen für Abrufmethoden" in [Grundlegendes zu Datentypkonvertierungen](../../../connect/jdbc/understanding-data-type-conversions.md) welcher [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentypen, die mit dieser Methode abgerufen werden können.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [getTime-Methode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/gettime-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement-Elemente](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement-Klasse](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
