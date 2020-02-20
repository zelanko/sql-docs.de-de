---
title: getBinaryStream (int) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getBinaryStream(int paramIndex)
apilocation:
- SQLServerCallableStatement.getBinaryStream(int paramIndex)
apitype: Assembly
ms.assetid: a766818e-cd05-4a07-a1ae-88966017448c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0e5e2a85e2db6dd89e571185712514a27621e835
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67953759"
---
# <a name="getbinarystream-int"></a>getBinaryStream (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft unter Berücksichtigung des Parameterindexes den Wert des angegebenen Parameters als Binärdatenstrom mit unterbrechungsfreien Bytes ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final java.io.InputStream getBinaryStream(int paramIndex)  
```  
  
#### <a name="parameters"></a>Parameter  
 *paramIndex*  
  
 Ein Wert vom Typ **int** zum Angeben des Parameterindexes.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein InputStream-Objekt  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [getBinaryStream-Methode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getbinarystream-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement-Elemente](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement-Klasse](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
