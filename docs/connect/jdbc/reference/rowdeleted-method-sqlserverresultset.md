---
title: rowDeleted-Methode (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.rowDeleted
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9c6db315-e614-4604-b020-41af6a214cc1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d4f761f4780b2fdb5da210db5bfb38d2368d865f
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80903926"
---
# <a name="rowdeleted-method-sqlserverresultset"></a>rowDeleted-Methode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ab, ob eine Zeile gelöscht wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean rowDeleted()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Der Wert lautet **TRUE**, falls eine Zeile gelöscht wurde und Löschungen erkannt werden. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese rowDeleted-Methode wird von der rowDeleted-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Eine gelöschte Zeile hinterlässt in einem Resultset ggf. eine sichtbare Lücke. Diese Methode kann verwendet werden, um Löcher in einem Resultset zu ermitteln. Der zurückgegebene Wert ist davon abhängig, ob vom [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt Löschungen ermittelt werden können.  
  
> [!NOTE]  
>  Gelöschte Zeilen werden von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zwar für alle aktualisierbaren Cursortypen erkannt, die Erkennung für Vorwärtscursor und dynamische Cursor ist jedoch kurzlebig.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
