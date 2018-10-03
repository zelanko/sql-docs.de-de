---
title: GetDate-Methode (java.util.Calendar) Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getDate (java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6d0deaf2-6f12-4a6e-b537-a51fa3478059
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 01babe87d330cabbfc6a882e1a22dd03ed99ff3e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47755238"
---
# <a name="getdate-method-javalangstring-javautilcalendar"></a>getDate-Methode (java.lang.String, java.util.Calendar)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft den Wert des angegebenen Parameters unter Berücksichtigung des Parameternamens und Calendar-Objekts als java.sql.Date-Objekt in der Programmiersprache Java ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.Date getDate(java.lang.String sCol,  
                             java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Parameter  
 *sCol*  
  
 Ein **String-Objekt**, das den Parameternamen enthält.  
  
 *CAL*  
  
 Ein Kalenderobjekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Date-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese getDate-Methode wird von der getDate-Methode in der java.sql.CallableStatement-Schnittstelle angegeben.  
  
 Von dieser Methode wird ein gültiger Datumsteil eines datetime- oder smalldatetime-Datentyps von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zurückgegeben. Der Zeitteil ist dabei auf die Java-Baseline (00:00, Mitternacht) festgelegt.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [getDate-Methode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getdate-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement-Elemente](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement-Klasse](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
