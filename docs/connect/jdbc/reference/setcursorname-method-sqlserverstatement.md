---
title: setCursorName-Methode (SQLServerStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.setCursorName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3f3ec4f2-103a-4e16-9206-c5bd8639f946
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a635fa491d800ac3955451fd0e3a3764ebb00590
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80924611"
---
# <a name="setcursorname-method-sqlserverstatement"></a>setCursorName-Methode (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den SQL-Cursornamen auf die angegebene Zeichenfolge fest, die dann für nachfolgende Ausführungsmethoden verwendet wird.  
  
> [!NOTE]  
>  Diese Methode wird von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] derzeit nicht unterstützt. Das Aufrufen der Methode hat keinerlei Wirkung.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final void setCursorName(java.lang.String name)  
```  
  
#### <a name="parameters"></a>Parameter  
 *name*  
  
 Eine **Zeichenfolge** mit dem Cursornamen.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese setCursorName-Methode wird von der setCursorName-Methode in der java.sql.Statement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerStatement-Elemente](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement-Klasse](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
