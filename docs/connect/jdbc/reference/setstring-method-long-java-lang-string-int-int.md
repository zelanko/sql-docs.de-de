---
description: setString-Methode (long, java.lang.String, int, int)
title: setString-Methode (long, java.lang.String, int, int) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerClob.setString (long, java.lang.String, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9fb59b09-e825-46a6-ba5d-85d4a8dc143a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 12b594a7cfd5133abde253123525161cc0d63273
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88355196"
---
# <a name="setstring-method-long-javalangstring-int-int"></a>setString-Methode (long, java.lang.String, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Schreibt die angegebene Zeichenfolge auf der Grundlage des angegebenen Offsets und der angegebenen Länge ab der angegebenen Position in das CLOB.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public int setString(long pos,  
                     java.lang.String str,  
                     int offset,  
                     int len)  
```  
  
#### <a name="parameters"></a>Parameter  
 *pos*  
  
 Die Position, an der Daten in das CLOB geschrieben werden sollen.  
  
 *str*  
  
 Die Zeichenfolge, die in das CLOB geschrieben werden soll.  
  
 *offset*  
  
 Das Offset innerhalb der Zeichenfolge, ab der Zeichen gelesen werden sollen.  
  
 *len*  
  
 Die Anzahl der zu schreibenden Zeichen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Anzahl der geschriebenen Zeichen.  
  
## <a name="exceptions"></a>Ausnahmen  
 java.sql.SQLException  
  
## <a name="remarks"></a>Bemerkungen  
 Diese setString-Methode wird von der setString-Methode in der java.sql.Clob-Schnittstelle angegeben.  
  
 Zeichendaten werden beginnend mit der angegebenen Position überschrieben, und sie können die ursprüngliche Länge des CLOB überschreiben. Durch Angeben eines Werts vom Typ "Position+1" wird die Zeichenfolge angefügt. Durch Angeben eines Werts vom Typ Position+2 oder größer (oder null oder weniger) wird ein Positionsfehler ausgelöst.  
  
## <a name="see-also"></a>Weitere Informationen  
 [setString-Methode &#40;SQLServerClob&#41;](../../../connect/jdbc/reference/setstring-method-sqlserverclob.md)   
 [SQLServerClob-Methoden](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [SQLServerClob-Elemente](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob-Klasse](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
