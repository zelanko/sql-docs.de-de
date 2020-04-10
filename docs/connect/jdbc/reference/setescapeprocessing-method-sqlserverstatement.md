---
title: setEscapeProcessing-Methode (SQLServerStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.setEscapeProcessing
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6ac0682e-e04c-4fdb-893b-92408d42051e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8b19314337fd78f85ab79d186c0d0956f0ed5aaa
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922364"
---
# <a name="setescapeprocessing-method-sqlserverstatement"></a>setEscapeProcessing-Methode (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den Escapeverarbeitungsmodus fest.  
  
> [!NOTE]  
>  Die Escapeverarbeitung für [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] ist immer aktiviert. Wird diese Methode auf "false" festgelegt, hat dies keine Auswirkungen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final void setEscapeProcessing(boolean enable)  
```  
  
#### <a name="parameters"></a>Parameter  
 *enable*  
  
 **TRUE**, um die Escapeverarbeitung zu aktivieren. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese setEscapeProcessing-Methode wird von der setEscapeProcessing-Methode in der java.sql.Statement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerStatement-Elemente](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement-Klasse](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
