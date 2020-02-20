---
title: getCursorName-Methode (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getCursorName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e5b3af67-423a-4551-a4c6-a4bc076bd504
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a4f57b300cb402f422b92330bfe33f1e3c61cf4f
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67984190"
---
# <a name="getcursorname-method-sqlserverresultset"></a>getCursorName-Methode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft den Namen des von diesem [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt verwendeten SQL-Cursors ab.  
  
> [!NOTE]  
>  Diese Methode wird von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] derzeit nicht unterstützt. Bei Aufruf wird eine Ausnahme ausgelöst.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.lang.String getCursorName()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Eine **Zeichenfolge** mit dem Cursornamen.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getCursorName-Methode wird von der getCursorName-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
