---
title: setNull Method (java.lang.String, int) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.setNull (java.lang.String, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e1d7e267-d9de-407a-b1a9-abdc2623478d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a2601c62446871d8abfb76f52e07b76600cbd054
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920897"
---
# <a name="setnull-method-javalangstring-int"></a>setNull-Methode (java.lang.String, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den angegebenen Parameter unter Berücksichtigung des festzulegenden Parametertyps auf einen NULL-Wert fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setNull(java.lang.String sCol,  
                    int nType)  
```  
  
#### <a name="parameters"></a>Parameter  
 *sCol*  
  
 Ein **String-Objekt**, das den Parameternamen enthält.  
  
 *nType*  
  
 Ein JDBC-Typcode, der durch ein java.sql.Types-Element definiert wird.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese setNull-Methode wird von der setNull-Methode in der java.sql.CallableStatement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [setNull-Methode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/setnull-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement-Elemente](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement-Klasse](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
