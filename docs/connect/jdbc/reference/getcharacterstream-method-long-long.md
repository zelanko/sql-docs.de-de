---
title: getCharacterStream-Methode (long, long) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d70f502f-f60f-436a-83e6-797a0ed71bf3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 66cb3ba13b24747075f85b32c8dd75854f6b57cd
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80907816"
---
# <a name="getcharacterstream-method-long-long"></a>getCharacterStream-Methode (long, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt die **CLOB**-Daten als Readerobjekt oder als Zeichendatenstrom mit der angegebenen Position und Länge zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.io.Reader getCharacterStream(long pos,  
                                         long length)  
```  
  
#### <a name="parameters"></a>Parameter  
 *pos*  
  
 Ein Wert vom Typ **long**, mit dem das Offset zum ersten Zeichen des abzurufenden Teilwerts angegeben wird.  
  
 *length*  
  
 Ein Wert vom Typ **long**, mit dem die Länge (in Zeichen) des abzurufenden Teilwerts angegeben wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Reader-Objekt, das die **Clob**-Daten enthält.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getCharacterStream-Methode wird von der getCharacterStream-Methode in der java.sql.Clob-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [getCharacterStream-Methode &#40;SQLServerClob&#41;](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverclob.md)   
 [SQLServerClob-Methoden](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [SQLServerClob-Elemente](../../../connect/jdbc/reference/sqlserverclob-members.md)  
  
  
