---
title: SetSQLXML-Methode (SQLServerPreparedStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 70bbdde0-75f7-4169-88c5-dbbe2c4bcd03
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a647e8fbae47e6687b6a2806f2046fab39fde13c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47754588"
---
# <a name="setsqlxml-method-sqlserverpreparedstatement"></a>setSQLXML-Methode (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den angegebenen Parameter auf das angegebene SQLXML-Objekt fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final void setSQLXML(int parameterIndex,  
                            java.sql.SQLXML xmlObject)  
```  
  
#### <a name="parameters"></a>Parameter  
 *parameterIndex*  
  
 Ein Wert vom Typ **int** zum Angeben des Parameterindexes.  
  
 *xmlObject*  
  
 Ein SQLXML-Objekt, das den Parameterwert enthält.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese setSQLXML-Methode wird von der setSQLXML-Methode in der java.sql.PreparedStatement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerPreparedStatement-Elemente](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
