---
title: getSQLXML-Methode (java.lang.String) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f56b192a-3255-4215-b552-8e494fbca083
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 474e50964628d7361f40ec9d5d296f8b410d7e52
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920451"
---
# <a name="getsqlxml-method-javalangstring"></a>getSQLXML-Methode (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft den Wert des angegebenen Parameters unter Berücksichtigung des Parameternamens als SQLXML-Objekt ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final java.sql.SQLXML getSQLXML(java.lang.String parameterName)  
```  
  
#### <a name="parameters"></a>Parameter  
 *parameterName*  
  
 Eine **Zeichenfolge** zum Angeben des Parameternamens.  
  
## <a name="return-value"></a>Rückgabewert  
 ASQLXMLobject.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getSQLXML-Methode wird von der getSQLXML-Methode in der java.sql.CallableStatement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [getSQLXML-Methode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getsqlxml-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement-Elemente](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
