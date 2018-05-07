---
title: UpdateNClob-Methode (java.lang.String, java.sql.NClob) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a025d124-3634-49fa-8bb5-e9b98f2d5de3
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a355e311847d1226174d268e6c5b864fa8a231b3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="updatenclob-method-javalangstring-javasqlnclob"></a>updateNClob-Methode (java.lang.String, java.sql.NClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aktualisiert die angegebene Spalte mit einem **NClob** Wert.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void updateNClob(java.lang.String columnLabel,  
                        java.sql.NClob x)  
```  
  
#### <a name="parameters"></a>Parameter  
 *columnLabel*  
  
 Ein **Zeichenfolge** , der die Bezeichnung der Spalte angibt.  
  
 *x*  
  
 Ein NClob-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Hinweise  
 Diese UpdateNClob-Methode wird von der UpdateNClob-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Diese Methode wird nur unterstützt unter **nvarchar(max)**, **Ntext**, und **Xml** Spalten. Bei Verwendung dieser Methode für andere Datentypen wird eine Ausnahme ausgelöst.  
  
## <a name="see-also"></a>Siehe auch  
 [UpdateNClob-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatenclob-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
