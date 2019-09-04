---
title: getNString-Methode (java.lang.String) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b351e999-85bf-498b-915a-f91d89134bce
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2d9362a41e5a48400c1b63d52b2ff89095d119d6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67981403"
---
# <a name="getnstring-method-javalangstring"></a>getNString-Methode (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft den Wert des angegebenen **NCHAR**-, **nvarchar**-oder **LONGNVARCHAR** -Parameters als Zeichenfolge in der Programmiersprache Java ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final java.lang.String getNString(java.lang.String parameterName)  
```  
  
#### <a name="parameters"></a>Parameter  
 *parameterName*  
  
 Ein **String-Objekt**, das den Parameternamen enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 AStringobject.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getNString-Methode wird von der getNString-Methode in der java.sql.CallableStatement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [getNString-Methode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getnstring-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement-Methoden](../../../connect/jdbc/reference/sqlservercallablestatement-methods.md)  
  
  
