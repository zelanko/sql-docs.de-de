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
manager: jroth
ms.openlocfilehash: 4dfd2c53ab5fb883edbaabbc33c8ac8255b284ed
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66799984"
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
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerClob-Methoden](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [SQLServerClob-Elemente](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob-Klasse](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
