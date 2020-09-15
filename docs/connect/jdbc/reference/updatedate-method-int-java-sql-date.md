---
description: updateDate-Methode (int, java.sql.Date)
title: updateDate(int, java.sql.Date)-Methode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateDate (int, java.sql.Date)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c5fb1292-a5cf-4cdd-8c4a-d1679944a6d0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: af27898aa87cdebcff9ffaa232e92bf4af230d47
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88353696"
---
# <a name="updatedate-method-int-javasqldate"></a>updateDate-Methode (int, java.sql.Date)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aktualisiert die angegebene Spalte mit einem Wert vom Typ "date" unter Berücksichtigung des Spaltenindexes.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void updateDate(int index,  
                       java.sql.Date x)  
```  
  
#### <a name="parameters"></a>Parameter  
 *Index*  
  
 Ein **ganzzahliger** Wert, der den Spaltenindex angibt.  
  
 *x*  
  
 Ein Datumswert.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese updateDate-Methode wird von der updateDate-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [updateDate-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatedate-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
