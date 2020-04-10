---
title: updateBlob(int, java.sql.Blob)-Methode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateBlob (int, java.sql.Blob)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1e86f588-1365-4011-9412-f0acf7009880
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9f255906e3e8397caa1199cd1988fe8fb36d2645
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80903320"
---
# <a name="updateblob-method-int-javasqlblob"></a>updateBlob-Methode (int, java.sql.Blob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aktualisiert die angegebene Spalte mit einem java.sql.Blob-Wert.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void updateBlob(int index,  
                       java.sql.Blob x)  
```  
  
#### <a name="parameters"></a>Parameter  
 *Index*  
  
 Ein **ganzzahliger** Wert, der den Spaltenindex angibt.  
  
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
  
  
