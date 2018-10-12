---
title: setNClob-Methode (java.lang.String, java.io.Reader) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a595679a-89b7-4b18-9ad2-d9cb13af2a28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9532a3f66fdc2be1254a612cecb7b33d3e0230de
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47773795"
---
# <a name="setnclob-method-javalangstring-javaioreader"></a>setNClob-Methode (java.lang.String, java.io.Reader)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den angegebenen Parameter auf das angegebene Readerobjekt fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final void setNClob(java.lang.String parameterName,  
              java.io.Reader reader)  
```  
  
#### <a name="parameters"></a>Parameter  
 *parameterName*  
  
 Ein **String-Objekt**, das den Parameternamen enthält.  
  
 *reader*  
  
 Ein Readerobjekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese Methode sollte verwendet werden, für die **NCHAR**, **NVARCHAR**, **NTEXT**, und **XML** Parameterdatentypen.  
  
 Diese setNClob-Methode wird von der setNClob-Methode in der java.sql.CallableStatement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [setNClob-Methode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/setnclob-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement-Elemente](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
