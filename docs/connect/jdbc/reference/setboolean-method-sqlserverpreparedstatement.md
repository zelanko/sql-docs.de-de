---
title: setBoolean-Methode (SQLServerPreparedStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setBoolean
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 63397a19-03a2-44bb-b661-7d62c95b6e4e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9742112df6732618eeef07c477af98ff033368fc
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80928811"
---
# <a name="setboolean-method-sqlserverpreparedstatement"></a>setBoolean-Methode (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den angegebenen Parameter auf den angegebenen Wert vom Typ **boolean** fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final void setBoolean(int n,  
                             boolean x)  
```  
  
#### <a name="parameters"></a>Parameter  
 *n*  
  
 Ein Wert **ganzzahliger** Wert zum Angeben der Parameternummer.  
  
 *x*  
  
 Bei diesem Wert handelt es sich um einen **booleschen** Wert, der entweder **TRUE** oder **FALSE** ist.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese setboolean-Methode wird von der setboolean-Methode in der java.sql.PreparedStatement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerPreparedStatement-Elemente](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement-Klasse](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
