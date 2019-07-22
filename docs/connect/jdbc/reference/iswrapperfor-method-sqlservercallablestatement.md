---
title: isWrapperFor-Methode (SQLServerCallableStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 71156863-3588-453e-b5a5-0573b2c1bebf
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5b1a572d3ab2dfba9d0aa0b8284fc770f3422782
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67977101"
---
# <a name="iswrapperfor-method-sqlservercallablestatement"></a>isWrapperFor-Methode (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt an, ob es sich bei diesem Anweisungsobjekt um einen Wrapper für die angegebene Schnittstelle handelt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean isWrapperFor(Class iface)  
```  
  
#### <a name="parameters"></a>Parameter  
 *iface*  
  
 Eine **Klasse** , die eine Schnittstelle definiert.  
  
## <a name="return-value"></a>Rückgabewert  
 **true** , wenn dieses Objekt die-Schnittstelle implementiert oder ein Objekt umschließt, das die-Schnittstelle implementiert. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Die [isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlservercallablestatement.md)-Methode und die [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlservercallablestatement.md)-Methode werden von der java.sql.Wrapper-Schnittstelle definiert, die in JDBC 4.0 eingeführt wird.  
  
 Wird von dieser Methode **true** zurückgegeben, kann [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlservercallablestatement.md) erfolgreich mit dem gleichen Argument aufgerufen werden.  
  
 Weitere Informationen finden Sie unter [Wrapper und Schnittstellen](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [unwrap-Methode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/unwrap-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement-Elemente](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement-Klasse](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
