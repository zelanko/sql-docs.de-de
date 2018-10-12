---
title: GetCharacterStream-Methode (long, Long) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d70f502f-f60f-436a-83e6-797a0ed71bf3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d875e82b4db5e1725f43307348d27a6701e2a88d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47697788"
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
 *POS*  
  
 Ein Wert vom Typ **long**, mit dem das Offset zum ersten Zeichen des abzurufenden Teilwerts angegeben wird.  
  
 *length*  
  
 Ein Wert vom Typ **long**, mit dem die Länge (in Zeichen) des abzurufenden Teilwerts angegeben wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Readerobjekt, enthält die **Clob** Daten.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese GetCharacterStream-Methode wird von der GetCharacterStream-Methode in der java.sql.Clob-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [getCharacterStream-Methode &#40;SQLServerClob&#41;](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverclob.md)   
 [SQLServerClob-Methoden](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [SQLServerClob-Elemente](../../../connect/jdbc/reference/sqlserverclob-members.md)  
  
  
