---
title: GetAsciiStream-Methode (SQLServerClob) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerClob.getAsciiStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 134abe5e-5add-4d27-b333-b4b0f4d94c31
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2490fc903f7c1c509adc1e6f776f00a39e5f4616
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47767268"
---
# <a name="getasciistream-method-sqlserverclob"></a>getAsciiStream-Methode (SQLServerClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Materialisiert das CLOB als ASCII-Datenstrom.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.io.InputStream getAsciiStream()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Eingabedatenstrom mit den CLOB-Daten.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese GetAsciiStream-Methode wird von der GetAsciiStream-Methode in der java.sql.Clob-Schnittstelle angegeben.  
  
 Gibt immer einen Bytestrom zurück und geht davon aus, dass die Daten im CLOB das ASCII-Format aufweisen, da nicht bekannt ist, ob es sich um Unicode oder eine andere Multibyte-Codeseite handelt.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerClob-Methoden](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [SQLServerClob-Elemente](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob-Klasse](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
