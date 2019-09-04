---
title: issparsecolumnset-Methode (SQLServerResultSetMetaData) | Microsoft-Dokumentation
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
ms.openlocfilehash: 2b902ddf8e9e05900e55492116ee9e22a3dbbccc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67977221"
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
 **true** , wenn eine Spalte in einem Resultset ein sparsespaltensatz ist, andernfalls **false**.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode ruft keine Informationen aus der Datenbank ab.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSetMetaData-Methoden](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [SQLServerResultSetMetaData-Elemente](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData-Klasse](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
