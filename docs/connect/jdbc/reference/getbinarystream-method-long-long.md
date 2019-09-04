---
title: getBinaryStream-Methode (Long, Long) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 30bc8882-04b4-4efd-95e4-7d3a2a8c1d47
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5cc12f9e7ed7a83363766355fa5d340a459a332b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67953651"
---
# <a name="getbinarystream-method-long-long"></a>getBinaryStream-Methode (long, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt unter Verwendung der angegebenen Startposition und Länge ein Eingabedatenstrom-Objekt mit einem BLOB-Teilwert zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.io.InputStream getBinaryStream(long pos, long length)  
```  
  
#### <a name="parameters"></a>Parameter  
 *pos*  
  
 Das Offset zum ersten Byte des abzurufenden Teilwerts.  
  
 *length*  
  
 Die Länge in Bytes des abzurufenden Teilwerts.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Eingabedatenstrom mit den BLOB-Daten.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getBinaryStream-Methode wird von der getBinaryStream-Methode in der Java. SQL. BLOB-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerBlob-Methoden](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [SQLServerBlob-Elemente](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [SQLServerBlob-Klasse](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
