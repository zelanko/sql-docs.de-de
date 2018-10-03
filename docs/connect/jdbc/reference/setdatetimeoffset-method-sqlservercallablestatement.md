---
title: SetDateTimeOffset-Methode (SQLServerCallableStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 9383e14d-c83e-43c5-980c-50a3e0bedc31
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0e739eb92c3c4b35d65399ad5665b42445e9df00
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47764714"
---
# <a name="setdatetimeoffset-method-sqlservercallablestatement"></a>setDateTimeOffset-Methode (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Diese Methode wurde in [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0 hinzugefügt.  
  
 Legt den Wert der angegebenen Spalte auf die [DateTimeOffset-Klasse](../../../connect/jdbc/reference/datetimeoffset-class.md) Wert.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setDateTimeOffset(String sCol, microsoft.sql.DateTimeOffset t)  
```  
  
#### <a name="parameters"></a>Parameter  
 *sCol*  
  
 Der Name einer Spalte.  
  
 *t*  
  
 Die [DateTimeOffset-Klasse](../../../connect/jdbc/reference/datetimeoffset-class.md) Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Sie können Abrufen einer [DateTimeOffset-Klasse](../../../connect/jdbc/reference/datetimeoffset-class.md) Wert mit einer [SQLServerCallableStatement.getDateTimeOffset](../../../connect/jdbc/reference/getdatetimeoffset-method-sqlservercallablestatement.md).  
  
 [SetDateTimeOffset](../../../connect/jdbc/reference/setdatetimeoffset-method-sqlserverpreparedstatement.md) nimmt die Ordnungszahl der Spalte.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerCallableStatement-Elemente](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement-Klasse](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
