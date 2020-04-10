---
title: setClob-Methode (java.lang.String, java.io.Reader, long) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: bc9fddea-134e-4440-ba54-a1f74bb40c46
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fbe5407948691ebe8d551e274e9ed29ace96350c
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80927115"
---
# <a name="setclob-method-javalangstring-javaioreader-long"></a>setClob-Methode (java.lang.String, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den angegebenen Parameter auf das angegebene Readerobjekt fest, dessen Länge der angegebenen Zeichenanzahl entspricht.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final void setClob(java.lang.String parameterName,  
            java.io.Reader value,  
            long length)  
```  
  
#### <a name="parameters"></a>Parameter  
 *parameterName*  
  
 Ein **String-Objekt**, das den Parameternamen enthält.  
  
 *value*  
  
 Ein Reader-Objekt  
  
 *length*  
  
 Ein Wert vom Typ **long** zum Angeben der Anzahl von Zeichen im Datenstrom.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese setClob-Methode wird von der setClob-Methode in der java.sql.CallableStatement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [setClob-Methode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/setclob-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement-Elemente](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
