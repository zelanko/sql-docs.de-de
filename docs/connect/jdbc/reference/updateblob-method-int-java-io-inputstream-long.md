---
description: updateBlob-Methode (int, java.io.InputStream, long)
title: updateBlob-Methode (int, java.io.InputStream, long) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2edf9b51-63e1-4c28-afdf-2d4af593d5f7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7dacb3d899e0833682671ff1c73d46f24caa3c1b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88353876"
---
# <a name="updateblob-method-int-javaioinputstream-long"></a>updateBlob-Methode (int, java.io.InputStream, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aktualisiert die angegebene Spalte unter Verwendung des angegebenen Eingabedatenstroms mit der angegebenen Anzahl von Bytes.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void updateBlob(int columnIndex,  
                       java.io.InputStream inputStream,  
                                              long length)  
```  
  
#### <a name="parameters"></a>Parameter  
 *columnIndex*  
  
 Ein **ganzzahliger** Wert, der den Spaltenindex angibt.  
  
 *inputStream*  
  
 Ein InputStream-Objekt  
  
 *length*  
  
 Ein Wert vom Typ **long** zum Angeben der Streamlänge.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese updateBlob-Methode wird von der updateBlob-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [updateBlob-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateblob-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
