---
title: getBytes-Methode (SQLServerBlob) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerBlob.getBytes
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bea1b810-b5c1-466d-bdc4-561468214632
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c4c7891c6d7454e0397406f9391fdfb60d0f0fc7
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "68213719"
---
# <a name="getbytes-method-sqlserverblob"></a>getBytes-Methode (SQLServerBlob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft die BLOB-Daten als Bytearray ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public byte[] getBytes(long pos,  
                       int length)  
```  
  
#### <a name="parameters"></a>Parameter  
 *pos*  
  
 Die Startposition, beginnend bei "1" (nicht "0").  
  
 *length*  
  
 Die Länge der abzurufenden Daten.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **byte**-Array mit den angeforderten Daten.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getBytes-Methode wird von der getBytes-Methode in der java.sql.Blob-Schnittstelle angegeben.  
  
 Bei einem BLOB, der NULL ist oder die Länge 0 besitzt, wird ein leeres **byte**-Array zurückgegeben (ein Bytearray der Länge „0“), wenn Sie versuchen, genau 0 Bytes an Position „1“ abzurufen.  
  
 Bei einem BLOB mit der Länge Null wird beim Versuch, eine beliebige Länge in Bytes an einer anderen Position als "1" abzurufen, eine Positionsausnahme ausgelöst.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerBlob-Methoden](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [SQLServerBlob-Elemente](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [SQLServerBlob-Klasse](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
