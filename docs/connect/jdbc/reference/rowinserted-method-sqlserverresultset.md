---
title: rowInserted-Methode (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.rowInserted
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e7c10372-0be8-4baa-87f7-ed6b66003357
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5b471631bb5111f6bc6af5889ecf0d4444e4742c
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80903853"
---
# <a name="rowinserted-method-sqlserverresultset"></a>rowInserted-Methode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ab, ob in der aktuellen Zeile eine Einfügung vorgenommen wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean rowInserted()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **TRUE**, wenn Elemente in eine Zeile eingefügt wurden und dies erkannt wurde. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese rowUpdated-Methode wird von der rowUpdated-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Der zurückgegebene Wert ist davon abhängig, ob vom [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt sichtbare Einfügungen ermittelt werden können.  
  
> [!NOTE]  
>  Von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] werden für Cursortypen keine eingefügten Zeilen ermittelt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
