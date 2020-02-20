---
title: getDateTimeOffset(int)-Methode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8bb00356-4d6e-4625-b924-67646930fdf2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ec297d1b01b6d7cf8d292d2f4518aa5b51cd9704
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67983837"
---
# <a name="getdatetimeoffset-method-int"></a>getDateTimeOffset-Methode (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Diese Methode wurde im JDBC-Treiber 3.0 für [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hinzugefügt.  
  
 Ruft den Wert der angegebenen Spalte unter Berücksichtigung des Parameterindexes als [DateTimeOffset-Klassenobjekt](../../../connect/jdbc/reference/datetimeoffset-class.md) in Java ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public microsoft.sql.DateTimeOffset getDateTimeOffset(int index)  
```  
  
#### <a name="parameters"></a>Parameter  
 *Index*  
  
 Die einsbasierte Ordnungszahl des Parameters.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein [DateTimeOffset-Klassenobjekt](../../../connect/jdbc/reference/datetimeoffset-class.md)  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Sie können einen Parameterwert der Klasse [DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) mit [SQLServerCallableStatement.setDateTimeOffset](../../../connect/jdbc/reference/setdatetimeoffset-method-sqlservercallablestatement.md) festlegen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [getDateTimeOffset-Methode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getdatetimeoffset-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement-Elemente](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement-Klasse](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
