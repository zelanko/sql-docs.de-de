---
title: setLastUpdateCount-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setLastUpdateCount
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5487631a-1107-4169-84ca-b77fd09bea66
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 930950a4aeffd733615be312808892bb10a82a31
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80925785"
---
# <a name="setlastupdatecount-method-sqlserverdatasource"></a>setLastUpdateCount-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt einen Wert vom Typ **Boolean** fest, mit dem angegeben wird, ob die lastUpdateCount-Eigenschaft aktiviert ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setLastUpdateCount(boolean lastUpdateCount)  
```  
  
#### <a name="parameters"></a>Parameter  
 *lastUpdateCount*  
  
 **TRUE**, wenn lastUpdateCount aktiviert ist. Andernfalls lautet der Wert **false**.  
  
## <a name="remarks"></a>Bemerkungen  
 Ist die lastUpdateCount-Eigenschaft auf **true** festgelegt, wird von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] nur die letzte Updatezählung aus einer an den Server übergebenen SQL-Anweisung zurückgegeben. Ist die lastUpdateCount-Eigenschaft auf **false** festgelegt, werden vom Treiber alle Updatezählungen zurückgegeben, einschließlich jener, die von möglicherweise ausgelösten Triggern zurückgegeben wurden. Ist die lastUpdateCount-Eigenschaft nicht festgelegt, wird von der [getLastUpdateCount](../../../connect/jdbc/reference/getlastupdatecount-method-sqlserverdatasource.md)-Methode der Standardwert **true** zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
