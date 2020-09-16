---
description: moveToCurrentRow-Methode (SQLServerResultSet)
title: moveToCurrentRow-Methode (SQLServerResultSet) | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7c5b26d92a64c8c9bfa952ac04a3a924c987d5f3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433192"
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
  
## <a name="remarks"></a>Bemerkungen  
 Diese moveToCurrentRow-Methode wird von der moveToCurrentRow-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Die Methode zeigt keine Auswirkungen, wenn der Cursor sich nicht in der Einfügezeile befindet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
