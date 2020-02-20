---
title: updateClob-Methode (java.lang.String, java.io.Reader) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 338a2bf2-b110-469d-ad08-a0f2bbefcb88
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7e4a50738cb7bca9feecaa647008713ee0899d66
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67999247"
---
# <a name="updateclob-method-javalangstring-javaioreader"></a>updateClob-Methode (java.lang.String, java.io.Reader)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aktualisiert die angegebene Spalte unter Verwendung des angegebenen Reader-Objekts.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void updateClob(java.lang.String columnLabel,  
                        java.io.Reader reader)  
```  
  
#### <a name="parameters"></a>Parameter  
 *columnLabel*  
  
 Eine **Zeichenfolge**, die die Spaltenbezeichnung enthält.  
  
 *reader*  
  
 Ein Reader-Objekt  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese updateClob-Methode wird von der updateClob-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [updateClob-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateclob-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
