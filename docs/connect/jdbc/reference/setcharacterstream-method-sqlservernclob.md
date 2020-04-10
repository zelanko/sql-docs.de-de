---
title: setCharacterStream-Methode (SQLServerNClob) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 09042ee9-dfb1-4d0b-82bd-d1224b0aea80
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a84aac6a02e3fabac2774a41ab8dfc8e99af8b25
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80927197"
---
# <a name="setcharacterstream-method-sqlservernclob"></a>setCharacterStream-Methode (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft einen Datenstrom ab, der verwendet wird, um ab der angegebenen Position einen Datenstrom von Unicode-Zeichen in den **NCLOB**-Wert zu schreiben, der von diesem **java.sql.NClob**-Objekt dargestellt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.io.Writer setCharacterStream(long pos)  
```  
  
#### <a name="parameters"></a>Parameter  
 *pos*  
  
 Die Position, ab der in den **NCLOB**-Wert geschrieben wird. Die erste Position ist „1“.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Writerobjekt, das für den Datenstrom steht, in den Unicode-codierte Zeichen geschrieben werden können.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese setCharacterStream-Methode wird von der setCharacterStream-Methode in der java.sql.NClob-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerNClob-Methoden](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob-Elemente](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob-Klasse](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
