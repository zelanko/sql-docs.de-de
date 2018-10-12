---
title: SetXopenStates-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setXopenStates
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9723591f-e987-426f-b70a-07f5c70dc094
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 65fde7feacb27f8c3b7fb2d809de4f75bc7e899c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47695868"
---
# <a name="setxopenstates-method-sqlserverdatasource"></a>setXopenStates-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt einen Wert vom Typ **Boolean** fest, mit dem angegeben wird, ob das Konvertieren von SQL-Status in XOPEN-kompatible Status aktiviert ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setXopenStates(boolean xopenStates)  
```  
  
#### <a name="parameters"></a>Parameter  
 *xopenStates*  
  
 **"true"** Wenn Konvertieren von SQL-Status in XOPEN-kompatible Status aktiviert ist. Andernfalls lautet der Wert **false**.  
  
## <a name="remarks"></a>Remarks  
 Ist die xopenStates-Eigenschaft auf **true** festgelegt, werden SQL-Status von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] in XOPEN-kompatible Status konvertiert. Durch den Standardwert **false** werden vom JDBC-Treiber SQL 99-Statuscodes zurückgegeben. Ist die xopenStates-Eigenschaft nicht festgelegt, wird von der [getXopenStates](../../../connect/jdbc/reference/getxopenstates-method-sqlserverdatasource.md)-Methode der Standardwert **false** zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
