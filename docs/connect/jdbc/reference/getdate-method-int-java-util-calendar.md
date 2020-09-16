---
description: getDate-Methode (int, java.util.Calendar)
title: getDate Method (int, java.util.Calendar) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getDate (int, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 38ce7b75-2623-4eff-bc18-8cf7193adec8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5db80d918f8f9b4757782c0f00aab8ece29239c3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88436422"
---
# <a name="getdate-method-int-javautilcalendar"></a>getDate-Methode (int, java.util.Calendar)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft den Wert des angegebenen Parameters unter Berücksichtigung des Parameterindexes und Calendar-Objekts als java.sql.Date-Objekt in der Programmiersprache Java ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.Date getDate(int index,  
                             java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Parameter  
 *Index*  
  
 Ein Wert vom Typ **int** zum Angeben des Parameterindexes.  
  
 *cal*  
  
 Ein Calendar-Objekt  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Date-Objekt  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getDate-Methode wird von der getDate-Methode in der java.sql.CallableStatement-Schnittstelle angegeben.  
  
 Diese Methode gibt einen gültigen Datumsteil eines  **datetime**- oder **smalldatetime**-Datentyps von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zurück. Der Zeitteil ist dabei auf die Java-Baseline 00:00 Uhr (Mitternacht) festgelegt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [getDate-Methode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getdate-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement-Elemente](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement-Klasse](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
