---
title: position(byte, long)-Methode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerBlob.position (byte[], long)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 787412c2-4342-49c8-9ca2-7a9ddcd3277c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 938254b8076d78ebd1ac768d130904077828aa03
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80914386"
---
# <a name="position-method-byte-long"></a>position-Methode (byte, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt die Position eines angegebenen Musters im BLOB auf der Grundlage des angegebenen **Bytearray**-Musters und des Startindexes zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public long position(byte[] bPattern,  
                     long start)  
```  
  
#### <a name="parameters"></a>Parameter  
 *bPattern*  
  
 Das zu suchende Muster.  
  
 *start*  
  
 Der Startindex, in dem gesucht werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert vom Typ **long** der Position, an der das Muster gefunden wurde oder „-1“, wenn es nicht gefunden wurde.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese position-Methode wird von der position-Methode in der java.sql.Blob-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [position-Methode &#40;SQLServerBlob&#41;](../../../connect/jdbc/reference/position-method-sqlserverblob.md)   
 [SQLServerBlob-Methoden](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [SQLServerBlob-Elemente](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [SQLServerBlob-Klasse](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
