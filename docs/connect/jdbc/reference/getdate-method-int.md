---
title: GetDate-Methode (Int) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getDate (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: aa9f08af-df24-4c80-8298-c4007339b20a
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e6c4defabb0397462d45f683d52ec9344ce4eefb
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42785981"
---
# <a name="getdate-method-int"></a>getDate-Methode (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft den Wert des angegebenen Parameters unter Berücksichtigung des Parameterindexes als java.sql.Date-Objekt in der Programmiersprache Java ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.Date getDate(int index)  
```  
  
#### <a name="parameters"></a>Parameter  
 *Index*  
  
 Ein Wert vom Typ **int** zum Angeben des Parameterindexes.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Date-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese getDate-Methode wird von der getDate-Methode in der java.sql.CallableStatement-Schnittstelle angegeben.  
  
 Von dieser Methode wird ein gültiger Datumsteil eines **datetime**- oder **smalldatetime**-Datentyps von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zurückgegeben. Der Zeitteil ist dabei auf die Java-Baseline (00:00, Mitternacht) festgelegt.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [getDate-Methode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getdate-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement-Elemente](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement-Klasse](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
