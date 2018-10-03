---
title: IsSparseColumnSet-Methode (SQLServerResultSetMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ac363670-78ae-49f1-aeda-4fba3329a258
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 54fb49527b8b755a884b779bd693044ee465c544
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47716868"
---
# <a name="issparsecolumnset-method-sqlserverresultsetmetadata"></a>isSparseColumnSet-Methode (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt an, ob eine Spalte in einem Resultset ein Satz von Sparsespalten ist.  
  
## <a name="syntax"></a>Syntax  
  
```scr  
public boolean isSparseColumnSet(int column)  
```  
  
#### <a name="parameters"></a>Parameter  
 *column*  
  
 Der Index der Spalte (mit der Basis eins).  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** Wenn eine Spalte in einem Resultset einen Spaltensatz mit geringer Dichte, andernfalls ist **"false"**.  
  
## <a name="remarks"></a>Remarks  
 Diese Methode ruft keine Informationen aus der Datenbank ab.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerResultSetMetaData-Methoden](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [SQLServerResultSetMetaData-Elemente](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData-Klasse](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
