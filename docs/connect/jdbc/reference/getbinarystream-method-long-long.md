---
title: GetBinaryStream-Methode (long, Long) | Microsoft-Dokumentation
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
manager: jroth
ms.openlocfilehash: e78a745e908399efa25e6f72faff9daec2cbd8ea
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66799790"
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
  
## <a name="remarks"></a>Remarks  
 Diese GetBinaryStream-Methode wird von der GetBinaryStream-Methode in der java.sql.Blob-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerBlob-Methoden](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [SQLServerBlob-Elemente](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [SQLServerBlob-Klasse](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
