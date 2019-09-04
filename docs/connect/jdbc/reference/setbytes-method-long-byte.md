---
title: SetBytes-Methode (Long, Byte) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerBlob.setBytes (long.byte[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ffb8f107-0f9d-4410-957f-62b718e1e872
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 02c8e541b237cbf72fc2b3da3ed5c2b0759b0eb2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67974911"
---
# <a name="setbytes-method-long-byte"></a>setBytes-Methode (long, byte)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Schreibt das angegebene Bytearray ab der angegebenen Position in das BLOB und gibt anschließend die Anzahl der geschriebenen Bytes zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public int setBytes(long pos,  
                    byte[] bytes)  
```  
  
#### <a name="parameters"></a>Parameter  
 *pos*  
  
 Die Position (1-basiert) im BLOB, ab der Daten geschrieben werden.  
  
 *bytes*  
  
 Das in den BLOB zu schreibende Bytearray.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert vom Typ **long**, der die Anzahl geschriebener Bytes angibt.  
  
## <a name="exceptions"></a>Ausnahmen  
 java.sql.SQLException  
  
## <a name="remarks"></a>Bemerkungen  
 Diese setBytes-Methode wird von der setBytes-Methode in der java.sql.Blob-Schnittstelle angegeben.  
  
 Daten werden beginnend mit der angegebenen Position überschrieben, und sie können die ursprüngliche Länge des BLOB übersteigen. Durch Angeben eines Werts vom Typ Position+1 werden Bytes an die Zeichenfolge angefügt. Durch Weitergeben eines Werts vom Typ Position+2 oder größer (oder null oder weniger) wird ein Positionsfehler ausgelöst. Durch Weitergeben eines **Bytearrays** mit einer Länge von NULL wird NULL zurückgegeben, weil keine Bytes geschrieben wurden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SetBytes- &#40;Methode SQLServerBlob&#41;](../../../connect/jdbc/reference/setbytes-method-sqlserverblob.md)   
 [SQLServerBlob-Methoden](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [SQLServerBlob-Elemente](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [SQLServerBlob-Klasse](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
