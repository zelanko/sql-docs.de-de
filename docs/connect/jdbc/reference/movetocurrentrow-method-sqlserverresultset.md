---
title: MoveToCurrentRow-Methode (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.moveToCurrentRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9a7c754c-2d72-4207-b3bd-2afc6047fb3d
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 0f0b3e779dd7d3164b8c9277a3d3437137827da6
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66779585"
---
# <a name="movetocurrentrow-method-sqlserverresultset"></a>moveToCurrentRow-Methode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Versetzt den Cursor an die gespeicherte Cursorposition (üblicherweise die aktuelle Zeile).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void moveToCurrentRow()  
```  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese MoveToCurrentRow-Methode wird von der MoveToCurrentRow-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Die Methode zeigt keine Auswirkungen, wenn der Cursor sich nicht in der Einfügezeile befindet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
