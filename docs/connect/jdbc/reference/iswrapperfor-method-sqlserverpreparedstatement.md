---
title: IsWrapperFor-Methode (SQLServerPreparedStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b0e591b1-73e2-4f90-967f-5555eadfc3f1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 37d08855ff496811c82b39aa19fc05d85864d9b3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47627991"
---
# <a name="iswrapperfor-method-sqlserverpreparedstatement"></a>isWrapperFor-Methode (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt an, ob es sich bei diesem Anweisungsobjekt um einen Wrapper für die angegebene Schnittstelle handelt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean isWrapperFor(Class iface)  
```  
  
#### <a name="parameters"></a>Parameter  
 *iface*  
  
 Ein **Klasse** definieren eine Schnittstelle.  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** Wenn dieses Objekt die Schnittstelle implementiert oder dient als Wrapper für ein Objekt, das die Schnittstelle implementiert. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Die [isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverpreparedstatement.md)-Methode und die [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverpreparedstatement.md)-Methode werden von der java.sql.Wrapper-Schnittstelle definiert, die in den JDBC 4.0-Spezifikationen eingeführt wird.  
  
 Wird von dieser Methode „true“ zurückgegeben, kann [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverpreparedstatement.md) erfolgreich mit dem gleichen Argument aufgerufen werden.  
  
 Weitere Informationen finden Sie unter [Wrapper und Schnittstellen](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [unwrap-Methode &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/unwrap-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement-Elemente](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement-Klasse](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
