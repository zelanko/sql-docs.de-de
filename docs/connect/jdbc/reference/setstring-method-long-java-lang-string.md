---
title: setString Method (long, java.lang.String) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerClob.setString (long, java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1b2190e9-5ace-497a-8554-0e913ea9b0cb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 64b1800ddd64358a9a6bcc11027391ef258b82a9
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80926638"
---
# <a name="setstring-method-long-javalangstring"></a>setString-Methode (long, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Schreibt die angegebene **Zeichenfolge** in das CLOB (beginnt bei der angegebenen Position).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public int setString(long pos,  
                     java.lang.String s)  
```  
  
#### <a name="parameters"></a>Parameter  
 *pos*  
  
 Die Position, an der Daten in das CLOB geschrieben werden sollen.  
  
 *s*  
  
 Die **Zeichenfolge**, die in das CLOB geschrieben werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Anzahl der geschriebenen Zeichen.  
  
## <a name="exceptions"></a>Ausnahmen  
 java.sql.SQLException  
  
## <a name="remarks"></a>Bemerkungen  
 Diese setString-Methode wird von der setString-Methode in der java.sql.Clob-Schnittstelle angegeben.  
  
 Zeichendaten werden beginnend mit der angegebenen Position überschrieben, und sie können die ursprüngliche Länge des CLOB übersteigen. Durch Angeben eines Werts vom Typ "Position+1" wird die Zeichenfolge angefügt. Durch Angeben eines Werts vom Typ „Position+2“ oder größer (oder null oder weniger) wird ein Positionsfehler ausgelöst.  
  
## <a name="see-also"></a>Weitere Informationen  
 [setString-Methode &#40;SQLServerClob&#41;](../../../connect/jdbc/reference/setstring-method-sqlserverclob.md)   
 [SQLServerClob-Methoden](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [SQLServerClob-Elemente](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob-Klasse](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
