---
title: setNull(int, int)-Methode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setNull (int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7e7f08e9-278a-495a-8ce3-ca173d055021
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f250113f83ea51c2705d81780c2207f63149a292
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920455"
---
# <a name="setnull-method-int-int"></a>setNull-MethodE (int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den angegebenen Parameter unter Berücksichtigung des festzulegenden Parametertyps auf einen NULL-Wert fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final void setNull(int index,  
                          int jdbcType)  
```  
  
#### <a name="parameters"></a>Parameter  
 *Index*  
  
 Ein Wert **ganzzahliger** Wert zum Angeben der Parameternummer.  
  
 *jdbcType*  
  
 Ein JDBC-Typcode, der durch ein java.sql.Types-Element definiert wird.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese setNull-Methode wird von der setNull-Methode in der java.sql.PreparedStatement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [setNull-Methode &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setnull-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement-Elemente](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement-Klasse](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
