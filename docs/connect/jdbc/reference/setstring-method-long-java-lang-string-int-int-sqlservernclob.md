---
description: setString-Methode (long, java.lang.String, int, int) (SQLServerNClob)
title: setString Method (long, java.lang.String, int, int) - NClob | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2d5e9f50-15b2-4c76-8bfc-3b5be49c2781
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1b28dc4e76be3d321f78cef7820a3c53480f08d8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88355276"
---
# <a name="setstring-method-long-javalangstring-int-int-sqlservernclob"></a>setString-Methode (long, java.lang.String, int, int) (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Schreibt die angegebene Zeichenfolge auf der Grundlage des angegebenen Offsets und der angegebenen Länge ab der angegebenen Position in das NCLOB.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
int setString(long pos,  
              java.lang.String str,  
              int offset,  
              int len)  
```  
  
#### <a name="parameters"></a>Parameter  
 *pos*  
  
 Die Position, ab der in das **NCLOB** geschrieben wird. Die erste Position ist „1“.  
  
 *str*  
  
 Die Zeichenfolge, die in das **NCLOB** geschrieben werden soll.  
  
 *offset*  
  
 Der Offset in *str*, ab dem die zu schreibenden Zeichen gelesen werden sollen.  
  
 *len*  
  
 Die Anzahl der zu schreibenden Zeichen.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese setString-Methode wird von der setString-Methode in der java.sql.NClob-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerNClob-Methoden](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob-Elemente](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob-Klasse](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
