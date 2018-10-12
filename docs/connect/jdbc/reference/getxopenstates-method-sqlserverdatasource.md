---
title: GetXopenStates-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getXopenStates
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: de6fdf6b-8345-4490-b35e-7115b61e782e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f40bd51344b7e3fcdac7712f53e7308657f6d9bc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47814428"
---
# <a name="getxopenstates-method-sqlserverdatasource"></a>getXopenStates-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt einen Wert vom Typ **boolean** zurück, mit dem angegeben wird, ob das Konvertieren von SQL-Status in XOPEN-kompatible Status aktiviert ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean getXopenStates()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** Wenn Konvertieren von SQL-Status in XOPEN-kompatible Status aktiviert ist. Andernfalls lautet der Wert **false**.  
  
## <a name="remarks"></a>Remarks  
 Ist die xopenStates-Eigenschaft auf **true** festgelegt, werden SQL-Status von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] in XOPEN-kompatible Status konvertiert. Durch den Standardwert **false** werden vom JDBC-Treiber SQL 99-Statuscodes zurückgegeben. Ist die xopenStates-Eigenschaft nicht festgelegt, wird von der getXopenStates-Methode der Standardwert **false** zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
