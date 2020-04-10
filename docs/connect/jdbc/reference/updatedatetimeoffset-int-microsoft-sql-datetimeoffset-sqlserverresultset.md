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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: debdb8bb5ddbe6c9c1646632a3f863d1c81c37d5
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80919824"
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
  
  
