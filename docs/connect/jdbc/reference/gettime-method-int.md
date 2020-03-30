---
title: getTime(int)-Methode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getTime (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6c13dea2-511f-48dc-b3db-2d3b72ccc9de
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6e0426a89de1e3cf78f1f41e45fc35ba81816362
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67979094"
---
# <a name="gettime-method-int"></a>getTime-Methode (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft den Wert des angegebenen Parameters unter Berücksichtigung des Parameterindexes als java.sql.Time-Objekt in der Programmiersprache Java ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.Time getTime(int index)  
```  
  
#### <a name="parameters"></a>Parameter  
 *Index*  
  
 Ein Wert vom Typ **int** zum Angeben des Parameterindexes.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Time-Objekt  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getTime-Methode wird von der getTime-Methode in der java.sql.CallableStatement-Schnittstelle angegeben.  
  
 Finden Sie im Diagramm, das mit dem Titel "Konvertierungen für Abrufmethoden" in [Grundlegendes zu Datentypkonvertierungen](../../../connect/jdbc/understanding-data-type-conversions.md) welcher [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentypen, die mit dieser Methode abgerufen werden können.  
  
## <a name="see-also"></a>Weitere Informationen  
 [getTime-Methode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/gettime-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement-Elemente](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement-Klasse](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
