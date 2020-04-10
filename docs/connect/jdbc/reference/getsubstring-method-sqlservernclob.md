---
title: getSubString-Methode (SQLServerNClob) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 1d91c930-1bac-4da9-b9a5-ac2cfd31541b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1f84e1ab88eee80a4d73cc04f301a7c588950c25
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80926168"
---
# <a name="getsubstring-method-sqlservernclob"></a>getSubString-Methode (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft eine Kopie der angegebenen Teilzeichenfolge im **NCLOB** auf der Grundlage der angegebenen Startposition und der Anzahl der zu kopierenden Zeichen ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.lang.String getSubString(long pos,  
                                  int length)  
```  
  
#### <a name="parameters"></a>Parameter  
 *pos*  
  
 Das erste Zeichen der zu extrahierenden Teilzeichenfolge. Das erste Zeichen befindet sich an Position 1.  
  
 *length*  
  
 Die Anzahl der aufeinanderfolgenden und zu kopierenden Zeichen.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine **Zeichenfolge**, bei der es sich um die angegebene Teilzeichenfolge im **NCLOB** handelt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getSubString-Methode wird von der getSubString-Methode in der java.sql.NClob-Schnittstelle angegeben.  
  
 Beim Versuch, null Zeichen aus einem leeren NCLOB oder aus einem NCLOB mit der Länge Null abzurufen, wird eine leere Zeichenfolge zurückgegeben. Beim Versuch, aus einem NCLOB mit der Länge Null eine beliebige Zeichenlänge an einer beliebigen Position (und nicht von Position 1) abzurufen, wird eine Positionsausnahme ausgelöst.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerNClob-Methoden](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob-Elemente](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob-Klasse](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
