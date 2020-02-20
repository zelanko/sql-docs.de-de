---
title: updateDateTimeOffset(int) (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 21ec0054-c808-4e88-9c8d-c71b696ce658
author: MightyPen
ms.author: genemi
ms.openlocfilehash: caad3533d06ad7c00a4fb2cd8000bdd12c51acdc
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67999118"
---
# <a name="updatedatetimeoffsetint-microsoftsqldatetimeoffset-sqlserverresultset"></a>updateDateTimeOffset(int, microsoft.sql.DateTimeOffset) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Diese Methode wurde im JDBC-Treiber 3.0 für [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hinzugefügt.  
  
 Aktualisiert bei einer vorhandenen nullbasierten Spaltenordinalzahl die für den Wert der [DateTimeOffset-Klasse](../../../connect/jdbc/reference/datetimeoffset-class.md) festgelegte Spalte.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void updateDateTimeOffset(int index, microsoft.sql.DateTimeOffset x)  
```  
  
#### <a name="parameters"></a>Parameter  
 *Index*  
  
 Die nullbasierte Ordinalzahl einer Spalte.  
  
 *x*  
  
 Ein [DateTimeOffset-Klassenobjekt](../../../connect/jdbc/reference/datetimeoffset-class.md)  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Sie können einen [DateTimeOffset Class](../../../connect/jdbc/reference/datetimeoffset-class.md)-Wert mit [SQLServerResultSet.getDateTimeOffset](../../../connect/jdbc/reference/getdatetimeoffset-sqlserverresultset.md) abrufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [updateDateTimeOffset &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatedatetimeoffset-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
