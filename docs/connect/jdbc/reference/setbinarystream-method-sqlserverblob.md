---
title: setBinaryStream-Methode (SQLServerBlob) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerBlob.setBinaryStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: abcec31f-1a60-4765-9725-8cf7e9f1f8ab
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4555dfb9256f3ffe2ba61e82fe90307991a5a580
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67975093"
---
# <a name="setbinarystream-method-sqlserverblob"></a>setBinaryStream-Methode (SQLServerBlob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft einen Datenstrom ab, mit dem in den BLOB-Wert geschrieben werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.io.OutputStream setBinaryStream(long pos)  
```  
  
#### <a name="parameters"></a>Parameter  
 *Pos*  
  
 Die Position im BLOB-Wert, an der geschrieben werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Ausgabedatenstrom.  
  
## <a name="exceptions"></a>Ausnahmen  
 java.sql.SQLException  
  
## <a name="remarks"></a>Remarks  
 Diese setBinaryStream-Methode wird von der setBinaryStream-Methode in der Java. SQL. BLOB-Schnittstelle angegeben.  
  
 Daten im BLOB werden beginnend mit der angegebenen Position vom Ausgabedatenstrom überschrieben, und sie können die ursprüngliche Länge des BLOB übersteigen. Durch Angeben eines Werts vom Typ Position+1 werden Bytes an die Zeichenfolge angefügt. Durch Weitergeben eines Werts vom Typ Position+2 oder größer (oder null oder weniger) wird ein Positionsfehler ausgelöst.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerBlob-Methoden](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [SQLServerBlob-Elemente](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [SQLServerBlob-Klasse](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
