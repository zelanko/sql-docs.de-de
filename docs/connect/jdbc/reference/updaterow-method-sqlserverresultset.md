---
title: updateRow-Methode (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- MSQLServerResultSet.updateRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: cfced0ca-a281-40dc-8d2f-370d5f0bf12b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c431c3f996ea5ba2f4a6868114919c949be95355
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80919659"
---
# <a name="updaterow-method-sqlserverresultset"></a>updateRow-Methode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aktualisiert die zugrunde liegende Datenbank mit dem neuen Inhalt der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void updateRow()  
```  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese updateRow-Methode wird von der updateRow-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Diese Methode kann nicht aufgerufen werden, wenn sich der Cursor in der Einfügezeile befindet.  
  
 Wird diese Methode aufgerufen, obwohl keine Spaltenwerte geändert wurden, wird eine Ausnahme ausgelöst.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
