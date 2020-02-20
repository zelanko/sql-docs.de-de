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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 17df08b401c7e1ae4e1f5d3b386808f11e3bb180
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67974296"
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
  
  
