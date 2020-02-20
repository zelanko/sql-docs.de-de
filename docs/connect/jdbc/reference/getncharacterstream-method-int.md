---
title: getNCharacterStream(int)-Methode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6ae704f5-823c-4dfe-8c08-07b547c61a3c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6ed91df645edd7083e0d91346dfdf6d39bebd91d
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67981650"
---
# <a name="getncharacterstream-method-int"></a>getNCharacterStream-Methode (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft den Wert des angegebenen Parameters unter Berücksichtigung des Parameterindexes als Readerobjekt ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final java.io.Reader getNCharacterStream(int parameterIndex)  
```  
  
#### <a name="parameters"></a>Parameter  
 *parameterIndex*  
  
 Ein Wert vom Typ **int** zum Angeben des Parameterindexes.  
  
## <a name="return-value"></a>Rückgabewert  
 AReaderobject.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode sollte beim Zugriff auf **NCHAR**-, **NVARCHAR**- und **LONGNVARCHAR**-Parameter verwendet werden.  
  
 Diese getNCharacterStream-Methode wird von der getNCharacterStream-Methode in der java.sql.CallableStatement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [getNCharacterStream-Methode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getncharacterstream-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement-Elemente](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
