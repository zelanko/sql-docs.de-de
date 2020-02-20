---
title: updateBlob-Methode (java.lang.String, java.sql.Blob) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateBlob (java.lang.String, java.sql.Blob)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: fdd47885-c7ec-4599-a645-ad0e082586f4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 945595e147825b0c9c026166fa14b2bbda90a20c
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67997092"
---
# <a name="updateblob-method-javalangstring-javasqlblob"></a>updateBlob-Methode (java.lang.String, java.sql.Blob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aktualisiert die angegebene Spalte mit einem java.sql.Blob-Wert.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void updateBlob(java.lang.String columnName,  
                       java.sql.Blob x)  
```  
  
#### <a name="parameters"></a>Parameter  
 *columnName*  
  
 Eine **Zeichenfolge**, die den Spaltennamen enthält.  
  
 *x*  
  
 Ein Blob-Objekt  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese updateBlob-Methode wird von der updateBlob-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [updateBlob-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateblob-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
